+++
date = '2025-06-18T11:12:14+05:00'
title = 'Cryptography(Encryption,Decryption)'
+++

> “Cryptography is the ultimate form of nonviolent direct action.”

# What is Cryptography?

**What is Cryptography?**  
Cryptography is the science of protecting information by turning it into unreadable code so that only the right person can read it.  
It keeps your data safe, private, and secure, whether it is stored or being sent across the internet.

**What is Decryption?**  
Decryption is the process of converting the coded (encrypted) message back into readable data, but only if you have the correct key.

**What is Encryption?**  
Encryption is the process of turning plain readable data into coded data so unauthorized people cannot understand it.

## Example:

**Plain text:** `HELLO`  
**Encrypted:** `KHOOR`  

This method of conversion of data is called **Caesar Cipher**.

### Simple Example: Caesar Cipher:

Caesar Cipher is a classic and easy method where each letter is shifted forward in the alphabet.

- **Plain Text:** `HELLO`  
- **Shift each letter +3:**
  - H → K  
  - E → H  
  - L → O  
  - L → O  
  - O → R  
- **Encrypted:** `KHOOR`

To decrypt it, shift the letters back by 3.

> This is a simple example that explains the encryption and decryption process.  
> In this example, we use the Caesar Cipher method, which is one of the oldest encryption techniques and is **not used in modern industry**.

# Modern Encryption / Decryption Techniques Used in the Industry:

In this section, we discuss the **modern techniques** of encryption and decryption used at the industry level.

## 1. AES (Advanced Encryption Standard):

- **Type:** Symmetric (same key for encryption and decryption)  
- **Used in:** File encryption, WhatsApp messages, databases, cloud storage  
- **Features:** Fast and secure  
- **Key Sizes:** 128, 192, or 256 bits

**Why is it important?**  
AES is trusted and super-efficient. It’s the most used method in apps, banks, and secure cloud storage.

## 2. RSA (Rivest-Shamir-Adleman):

- **Type:** Asymmetric (public and private key pair)  
- **Used in:** SSL certificates, secure emails, digital signatures  
- **Features:** Secure but slower than AES

**Why is it important?**  
RSA is great for sending secrets without sharing a key in advance. It is used to protect data on websites and apps.

## 3. TLS/SSL (Transport Layer Security / Secure Sockets Layer):

- **Type:** Protocol (uses RSA or ECC + AES)  
- **Used in:** `https://` websites, online banking, secure messaging  
- **Features:** Ensures data is encrypted between you and a server

**Why is it important?**  
TLS/SSL keeps your data safe during online communication, like when you log into a bank or make a purchase.

## 4. ECC (Elliptic Curve Cryptography):

- **Type:** Asymmetric (like RSA, but smaller & faster)  
- **Used in:** Mobile apps, cryptocurrency wallets, secure messaging  
- **Features:** Lightweight – great for mobile and IoT devices

**Why is it important?**  
ECC offers strong security like RSA but with smaller key sizes, making it ideal for modern, mobile-first tech.

## 5. Hashing:

- **Type:** One-way (can’t be decrypted)  
- **Used in:** Password protection, data verification, blockchain  
- **Features:** Stores only the "fingerprint" of data

**Why is it important?**  
Hashing secures sensitive data like passwords. Even if a hacker steals a database, they cannot reverse the hash.

# Which Method is Used in Big Data Centers?

**AES-256** is the most widely used encryption method in big data centers and cloud platforms like **Google Cloud**, **AWS**, and **Azure** because:

- It is fast  
- Highly secure  
- Works well with large volumes of data

# Comparison Between the Different Encryption/Decryption Methods:

| Method | Type      | Used For                  | Can Be Decrypted? | Speed | Security Level | Simple Explanation |
|--------|-----------|---------------------------|-------------------|-------|----------------|--------------------|
| AES    | Symmetric | File & message encryption | Yes               | Fast  | Very Strong    | Same key is used to encrypt and decrypt. Used in apps, cloud storage, and databases. |
| RSA    | Asymmetric| Emails, digital signatures, SSL | Yes         | Slower| Very Strong    | Uses public & private keys. Great for securely sharing encryption keys. |
| TLS/SSL| Protocol  | Secure websites (HTTPS)   | Yes               | Fast  | Strong         | A protocol that uses RSA/ECC + AES to protect online communication. |
| ECC    | Asymmetric| Mobile apps, blockchain   | Yes               | Fast  | Very Strong    | Like RSA, but faster and lighter. Ideal for mobile and IoT devices. |
| Hashing| One-way   | Passwords, blockchain     | No                | Fast  | Unbreakable    | Turns data into fixed-length code. Cannot be reversed. Used for secure login and verification. |

# Final Thoughts:

In today's digital world, protecting information is more important than ever.

Cryptography, through encryption and decryption, plays a key role in keeping our data private and secure. Whether it is **AES for fast and strong encryption**, **RSA for secure key exchange**, or **hashing for protecting passwords**, each method has its own purpose and strength.

> Understanding these techniques is the first step toward a career in cybersecurity.  
> As technology evolves, so do the threats, and knowing how to secure data is a skill in high demand across every industry.

---

> _"In the world of cybersecurity, encryption isn't just protection — it's trust written in code."_

**Thank You!**

