# Mail Server
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

## Basic Postfix Configuration

The following are the initial configurations made to the Postfix `main.cf` file to set up a basic mail server:

- **myhostname**:  
  Set to `mail.mymail.com` to define the fully qualified domain name of the mail server.  

- **myorigin**:  
This defines the domain that will appear in the "From" address of outgoing emails. In this case, the domain is set to `mymail.com`. 

- **inet_interfaces**:  
Configured to allow the server to listen on all network interfaces for incoming mail. It is set to `all`.  

- **mydestination**:  
Specifies the domains for which the mail server will accept emails. In this case, it accepts emails for its own hostname and the domain `mymail.com`. In this case, it is set to `$myhostname, mymail.com, localhost`.

- **home_mailbox**:  
Configured to use the `Maildir/` format for storing user emails. This allows the mails to be stored in the user's home directory.

- **Save the file**.
- Restart postfix with `sudo systemctl restart postfix`.
     
## Dovecot Configuration for IMAP (Port 143)

In this project, Dovecot is configured to handle incoming mail via IMAP on port 143, allowing clients like Thunderbird to access the inbox.

#### Changes Made:
1. **Enabled IMAP (Port 143)**: 
   - In the Dovecot configuration file (`/etc/dovecot/conf.d/10-master.conf`), the comments were removed from the lines that specify the IMAP service and port:
   ```bash
   service imap-login {
       inet_listener imap {
           port = 143
       }
   }
2. **Save the file**.
3. Restart dovecot with `sudo systemctl restart dovecot`.
4. **Client Testing**:
   - Thunderbird was used as the email client to connect to Dovecot via IMAP, successfully receiving emails in the inbox.

## Usage
- Test sending an email using Postfix.
- Check received emails using Dovecot.


