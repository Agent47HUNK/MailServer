# MailServer
Initial basic configuration of Mail server in Fedora 21. 

## Overview
- This project demonstrates setting up a mail server using Postfix and Dovecot in a Proxmox environment on a Linux system.
- The configuration allows for sending and receiving emails across different mail servers within the virtual environment.

## Prerequisites
- Linux (e.g., Ubuntu, CentOS, Fedora)
- Postfix
- Dovecot
- Basic understanding of terminal and networking.

## Installation

1. **Install Postfix:**
   - `sudo yum install postfix`

2. **Install Dovecot:**
   - `sudo yum install dovecot`
  
## Configuration Files
- **Postfix (`main.cf`)**:
  - Configuration for mail transport.

- **Dovecot (`10-master.conf`)**:
  - Configuration for handling mail delivery and access.

## Usage
- Test sending an email using Postfix.
- Check received emails using Dovecot.


