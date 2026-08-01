# Applying-Cryptography-Real-World-Scenarios

## Overview
A hands-on implementation of core cryptographic techniques using OpenSSL 
on Kali Linux. The project demonstrates how cryptography protects modern 
information systems through symmetric encryption, hashing, asymmetric 
encryption, digital signatures, and a real-world file verification scenario.

## Objectives
- Demonstrate data protection using AES-256-CBC symmetric encryption
- Verify data integrity using SHA-256 hashing
- Implement secure messaging using RSA-2048 asymmetric encryption
- Demonstrate authenticity through digital signatures
- Simulate a real-world file verification system

## Tools Used
| Tool | Purpose |
|---|---|
| Kali Linux | Operating environment |
| OpenSSL 3.5.5 | All cryptographic operations |
| SHA-256 | Hashing and integrity verification |
| AES-256-CBC | Symmetric encryption |
| RSA-2048 | Asymmetric encryption and digital signatures |

## What Was Done

### 1. AES-256-CBC Encryption — Confidentiality
Created a plaintext file and encrypted it using AES-256-CBC. Inspected 
the output using od -c which confirmed the file was completely unreadable 
ciphertext. Decrypted the file back to the original plaintext and verified 
an exact match.

**Key Command:**
openssl enc -aes-256-cbc -salt -pbkdf2 -in original_message.txt -out encrypted_file.enc

**What it protects:** Confidentiality — only someone with the key can read the data.

### 2. SHA-256 Hashing — Integrity
Generated a SHA-256 hash of a file. Added a single period to the file 
and hashed it again. The output was completely different — demonstrating 
the Avalanche Effect.

**What it protects:** Integrity — any change to the file, no matter how 
small, produces a completely different hash.

### 3. RSA-2048 Asymmetric Encryption — Secure Messaging
Generated a 2048-bit RSA key pair. Encrypted a message using the public 
key and decrypted it using the private key. Confirmed the original message 
was recovered exactly.

**Key permissions observed:**
- Private key: rw------- (owner only)
- Public key: rw-rw-r-- (readable by anyone)

**What it protects:** Secure communication — anyone can encrypt using the 
public key but only the private key holder can decrypt.

### 4. Digital Signatures — Authenticity
Signed a file using the private key. Verified the signature using the 
public key — result: Verified OK. Modified the file and attempted 
verification again — result: Verification failure. 

**What it protects:** Authenticity and integrity — proves who sent the 
file and that it has not been tampered with.

### 5. Real-World File Verification System
Downloaded the official Linux kernel README from Linus Torvalds' GitHub 
repository. Generated and saved its SHA-256 hash. Injected malware text 
into the file — hash check returned FAILED. Re-downloaded the clean file 
— hash check returned OK.

**Real-world equivalent:** Package managers like apt and pip use this 
exact process to verify every software download.

## What Each Method Protects
| Method | CIA Property | Real-World Example |
|---|---|---|
| AES-256-CBC | Confidentiality | Bank data at rest, WhatsApp media |
| SHA-256 | Integrity | Software downloads, audit logs |
| RSA-2048 | Authenticity | SSL certificates, code signing |
| Digital Signature | Authenticity + Integrity | Government IDs, financial transactions |

## Skills Demonstrated
- Symmetric and asymmetric encryption
- Cryptographic hashing and integrity verification
- Digital signature creation and verification
- OpenSSL command-line cryptography
- Real-world application of cryptographic concepts
- Digital signature creation and verification
- OpenSSL command-line cryptography
- Real-world application of cryptographic concepts
