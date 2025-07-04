
+++
date = '2025-07-3'
title = 'System Monitoring'
+++

# System Monitoring

> "You can't manage what you can't measure — system monitoring turns invisible problems into visible opportunities."

## What is Monit?

Monit is an open-source utility designed to monitor and manage Unix system processes. It allows system administrators to automatically monitor system resources, files, directories, services, and daemons like Apache, MySQL, and others. If a service fails, Monit can automatically restart it, alert the admin, or execute custom scripts — all without manual intervention.

## What is a Monitoring System?

A monitoring system is a tool or set of tools used in system administration to continuously observe and track the performance, availability, and health of applications, services, and infrastructure. It ensures:

- System uptime
- Resource usage tracking (CPU, memory, disk)
- Process health checks
- Service availability
- Automated alerts and recovery

In System Monitoring we use different tools. One of the best tools that we use is Monit.

## How does Monit perform its monitoring tasks in a Linux system?

Monit operates by running in the background as a daemon. It reads from a configuration file (`/etc/monit/monitrc`) to determine which processes or services to monitor and how often to check their status. When an issue is detected (e.g., a crashed service), Monit takes predefined actions such as restarting the service, sending alerts, or executing scripts.

## How is Monit useful in system administration?

Monit is a powerful assistant for sysadmins, helping with:

- Automatic service recovery (restart if failed)
- Email alerts when something breaks
- Resource usage tracking (RAM, CPU, disk)
- Web-based dashboard to see system health
- Monitoring specific services like Apache or MySQL with custom rules

## Key Advantages of Monit:

- Lightweight and easy to configure
- Real-time monitoring
- Automatic problem resolution
- Simple syntax for configuration
- Built-in web interface
- Works at both system and service level

## System-Wide vs. Service-Specific Monitoring with Monit:

Monit can be configured in two main ways:

**System-wide monitoring**: Tracks overall system metrics — CPU load, memory usage, disk usage, uptime, etc.

**Service-specific monitoring**: Targets specific services like Apache, MySQL, SSH, etc. You can define custom checks such as:

- Is the process running?
- Is the port open?
- Is the response time under a limit?
- Is the log file too big?

## Practical Implementation of Monit

### STEP 1: Install Monit, Apache, and MySQL

Apache Installation:

```bash
sudo apt install apache2
```

MySQL Installation:

```bash
sudo apt install mysql-server
```

Monit Installation:

```bash
sudo apt install monit
```

Example output:

```bash
~$ sudo apt install monit -y
[sudo] password for khansa: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
...
Processing triggers for man-db (2.10.2-1) ...
```

> Note: Apache2 and MySQL must be installed beforehand if you want to monitor them.

### STEP 2: Enable Services to Start at Boot

```bash
sudo systemctl enable apache2
sudo systemctl enable mysql
sudo systemctl enable monit
```

### STEP 3: Start the Services

```bash
sudo systemctl start apache2
sudo systemctl start mysql
sudo systemctl start monit
```

### STEP 4: Configure Monit Web Interface

Edit Monit Main Configuration:

```bash
sudo nano /etc/monit/monitrc
```

Uncomment the following lines:

```monit
set httpd port 2812 and
    use address localhost
    allow localhost
    allow admin:monit
```

### STEP 5: Check Monit Configuration

```bash
sudo monit -t
```

Output:

```text
Control file syntax OK
```

### STEP 6: Restart Monit

```bash
sudo systemctl restart monit
```

### STEP 7: Create Service Monitoring Configs

**Apache Monitoring Config**

```bash
sudo nano /etc/monit/conf-enabled/apache.monit
```

Paste the following:

```monit
check process apache2 with pidfile /run/apache2/apache2.pid
   start program = "/usr/sbin/service apache2 start"
   stop program  = "/usr/sbin/service apache2 stop"
   if failed port 80 protocol http then restart
   if 5 restarts within 5 cycles then timeout
```

**MySQL Monitoring Config**

```bash
sudo nano /etc/monit/conf-enabled/mysql.monit
```

Paste the following:

```monit
check host mysql with address 127.0.0.1
   start program = "/usr/sbin/service mysql start"
   stop program  = "/usr/sbin/service mysql stop"
   if failed port 3306 protocol mysql then restart
```

### STEP 8: Reload Monit

```bash
sudo monit reload
```

### STEP 9: Access Monit Dashboard

Visit [http://localhost:2812](http://localhost:2812) in your browser.

**Username:** `admin`  
**Password:** `monit`

### STEP 10: Check Status via CLI

```bash
sudo monit status
```

Example output:

```
Monit 5.31.0 uptime: 15m

Process 'mysqld'
  status                       Initializing
  monitoring status            Initializing
  ...

Process 'apache2'
  status                       OK
  monitoring status            Monitored
  ...
```

## Stopping Services

**Stop Monit:**

```bash
sudo systemctl stop monit
```

**Disable Monit on Boot:**

```bash
sudo systemctl disable monit
```

**Stop MySQL:**

```bash
sudo systemctl stop mysql
sudo systemctl disable mysql
```

**Stop Apache:**

```bash
sudo systemctl stop apache2
sudo systemctl disable apache2
```

---

In today's digital landscape, effective system monitoring is not just a best practice — it's a necessity. It enables organizations to maintain performance, ensure security, and respond proactively to issues before they escalate. A well-monitored system lays the foundation for operational excellence and business continuity.

> "You can't manage what you can't measure — system monitoring turns invisible problems into visible opportunities."
