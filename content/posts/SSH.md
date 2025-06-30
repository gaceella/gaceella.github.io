
+++
date = '2025-06-29'
title = 'Secure Remote Access(SSH)'
+++

# Secure Remote Access (SSH)

SSH (Secure Shell) is a secure way to connect to another computer over a network. It allows you to remotely access and control a system as if you were using it directly, while encrypting the connection to keep data safe from hackers.

---

## How SSH Works

- **Encrypted Connection**: SSH creates a secure, encrypted link between your computer and the remote system, protecting your data from unauthorized access.
- **Remote Access & Control**: After connecting, you can run commands, transfer files, and manage the remote computer as if you were physically using it.

---

## Activation of SSH on Windows

If you're on **Windows**, you can use **PuTTY** to access SSH. It provides a terminal where you can run SSH commands.  
For **mobile devices**, **Termux** creates a Linux-like environment for SSH access.

---

## Activation of SSH on Linux (Ubuntu)

These are the steps to make an SSH connection with your own system.

### Step 1: Install Net Tools

```bash
sudo apt update && sudo apt install -y net-tools
```

### Step 2: Install OpenSSH Server

```bash
sudo apt install -y openssh-server
```

### Step 3: Start & Enable SSH Service

```bash
sudo systemctl enable ssh
sudo systemctl start ssh
```

### Step 4: Check SSH Service Status

```bash
sudo systemctl status ssh
```

### Step 5: Find Your System’s IP

```bash
ifconfig
```

### Step 6: Connect to Your Own System

```bash
ssh username@127.0.0.1
```

> Replace `username` and `127.0.0.1` with your actual system username and IP address.

### Step 7: Exit SSH Session

```bash
exit
```

---

## Connect to a Remote Machine

### Step 1: Ensure Same Network

Make sure **both systems** (your local and the remote machine) are on the **same network** or connected through the internet.

### Step 2: Install OpenSSH on Remote Machine

```bash
sudo apt update && sudo apt install -y openssh-server
```

### Step 3: Start & Enable SSH Service

```bash
sudo systemctl enable ssh
sudo systemctl start ssh
```

### Step 4: Find Remote IP Address

```bash
ifconfig
# or
hostname -I
```

### Step 5: Exit from Remote Machine

```bash
exit
```

---

## Passwordless SSH Login

Passwordless SSH login uses **SSH key pairs** instead of passwords. The **private key** remains on your machine, while the **public key** is stored on the remote system.

### Benefits

- More secure than using passwords
- Eliminates brute-force risks
- Enables automated and faster login

### Step 1: Generate SSH Keys

```bash
ssh-keygen -t ed25519 -C "SSHKEY"
```

> Press `ENTER` to skip the passphrase.

### Step 2: Copy Public Key to Remote Server

```bash
ssh-copy-id username@ip_address
```

> Replace `username` and `ip_address` with the remote system's details.

### Step 3: Connect Passwordlessly

```bash
ssh username@ip_address
```

> You’ll only enter the password once during `ssh-copy-id`.

### Step 4: Exit SSH Session

```bash
exit
```

---

## File Transfer Using SSH

You can transfer files from a **local system to a remote system** using `scp` or `rsync`.

### Method 1: Using SCP (Secure Copy Protocol)

```bash
scp local_file username@remote_ip:/remote/directory
```

### Method 2: Using Rsync (Remote Sync)

```bash
rsync -avz local_directory username@remote_ip:/remote/directory
```

---

## SCP vs Rsync: Which One to Use?

- **Use SCP** for **quick file transfers**.
- **Use Rsync** for **large transfers, backups**, and **resumable syncs**.

> **Recommended**: Rsync is usually the better choice due to speed, syncing ability, and resume capability.

---

> _"Technology is best when it brings people together."_

**Thank You!**
