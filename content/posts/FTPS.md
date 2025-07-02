
+++
date = '2025-07-01'
title = 'File Transfer Protocol Secure (FTPS)'
+++




# File Transfer Protocol Secure (FTPS)

> "In the digital age, securing data in transit isn't optional—it's foundational. FTPS turns simple file sharing into secure communication."

## What is FTP?
FTP stands for **File Transfer Protocol**.  
It is used to send or receive files between two computers over a network.

- It allows actions like uploading, downloading, and deleting files.
- It is not secure — everything, including usernames and passwords, is sent as plain text.

## What is FTPS?
FTPS means **File Transfer Protocol Secure**.  
It is just like FTP but with added security.

- FTPS uses **TLS or SSL** encryption to protect your data.
- It keeps your files, login information, and other data safe during transfer.
- FTPS is often used in businesses where security is important.

## Why do we use FTPS instead of FTP?
We use FTPS because it is more secure than normal FTP.

- FTP is not safe — everything is visible to hackers.
- FTPS encrypts the data using TLS/SSL, so:
  - Passwords and files are not readable to others.
  - It protects against hackers and data leaks.
  - It also helps follow rules like **HIPAA** or **GDPR**.

## Advantages of FTPS

1. **Data is Encrypted**: Your files and passwords are protected.
2. **Better Security**: No one can read or steal your data while it's moving.
3. **Authentication**: Only allowed users can access the server.
4. **Supports Compliance**: Meets security rules required by many industries.

## Disadvantages of FTP (Not FTPS)

1. **No Encryption**: Everything is sent in plain text.
2. **Not Secure**: Hackers can easily steal your info.
3. **No Data Protection**: Files can be changed without you knowing.
4. **Bad for Sensitive Info**: Should not be used for private or business data.

## FTPS is Good, But One Limitation:
FTPS is safe and secure, but there is one important problem to know:

### FTPS Needs a Trusted TLS/SSL Certificate:

- FTPS needs a TLS/SSL certificate to work securely.
- For real use (production), this certificate must be from a **trusted Certificate Authority**.
- These certificates are usually **paid**.

## What if We Are Just Testing?
If you are just testing FTPS (e.g., on your own computer), you can:

- Use a **self-signed certificate** created with OpenSSL.
- You can be both the server and the client on your own PC.

### The Problem With Self-Signed Certificates:

- FTPS clients (like FileZilla) do not trust self-signed certificates.
- This can cause:
  - Warnings
  - Connection errors
  - Security issues

> Even in testing, you must set up proper usernames and passwords.

## Steps for Beginners

### STEP 1: Install openssl and vsftpd on the server

```bash
sudo apt update
sudo apt install vsftpd openssl
```

### STEP 2: Install lftp on the client

```bash
sudo apt install lftp
```

## Server Configuration

### STEP 3: Generate SSL certificate (self-signed)

```bash
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
-keyout /etc/ssl/private/vsftpd.key \
-out /etc/ssl/certs/vsftpd.pem
```

**Certificate Paths:**

- Certificate: `/etc/ssl/certs/vsftpd.pem`
- Private Key: `/etc/ssl/private/vsftpd.key`

> This self-signed certificate is valid for 365 days.

When prompted, enter your name, email, and **IP as common name**, e.g., `192.168.1.10`.

### STEP 4: Configure vsftpd to use FTPS

```bash
sudo nano /etc/vsftpd.conf
```

Paste this configuration:

```ini
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
chroot_local_user=YES

ssl_enable=YES
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
rsa_private_key_file=/etc/ssl/private/vsftpd.key
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
require_ssl_reuse=NO
ssl_ciphers=HIGH
```

Save with `Ctrl+O`, press `ENTER`, and exit with `Ctrl+X`.

### STEP 5: Restart the vsftpd service

```bash
sudo systemctl restart vsftpd
sudo systemctl status vsftpd
```

You should see `ACTIVE` status.

### STEP 6: Confirm FTP port is listening (Port 21)

```bash
sudo netstat -tulnp | grep vsftpd
```

### STEP 7: Create FTP User

```bash
sudo adduser ftptest
```

> Create a password and remember it for login.

### STEP 8: 💻 Client-Side: Create a test file

```bash
echo "Hello from client" > testfile.txt
```

### STEP 9: Connect to FTPS Server Using lftp

```bash
lftp -u ftptest,khan1234 ftp://192.168.1.10
```

Inside lftp prompt, run:

```bash
set ssl:verify-certificate no
set ftp:ssl-force true
set ftp:ssl-protect-data true
set ftp:passive-mode true
```

### STEP 10: Upload the file

```bash
put testfile.txt
```

Expected output:

```
18 bytes transferred
```

### STEP 11: Verify file on server

```bash
ls
```

Expected output:

```
-rw-------    1 1002     1002           18 Jun 05 07:01 testfile.txt
```

### STEP 12: Download the file

```bash
get testfile.txt
```

To overwrite if exists:

```bash
set xfer:clobber yes
get testfile.txt
```

Or download with new name:

```bash
get testfile.txt -o testfile_copy.txt
```

### STEP 13: Exit the lftp session

```bash
exit
```

### STEP 14: Check file content on client

```bash
cat testfile.txt
```

Expected output:

```
Hello from client
```

---

As technology evolves, file transfer remains a core function of digital communication. FTP offers the foundation, and FTPS strengthens it with security—making your data exchange both fast and safe.

> "It’s not just about moving files—it’s about moving them safely. Choose FTPS, because your data deserves protection on every path."

**THANK YOU!**