
# How to set up a OpenSSH server

This guide provides step-by-step instructions for installing and configuring an OpenSSH server on a Linux machine. OpenSSH (Open Secure Shell) allows secure remote login and other network services over an encrypted communication. It is widely used for secure remote administration and file transfers across different platforms. This guide assumes basic familiarity with the Linux shell.

## Installation

**First you need to get OpenSSH (Skip if already installed)**

For Ubuntu/Debian:
```bash
sudo apt update
sudo apt install openssh-server
```
For CentOS/RHEL:    
```bash
sudo yum install openssh-server
```
For Fedora:
```bash
sudo dnf install openssh-server
```
## Start and Enable the SSH Service
**After installation, start the SSH service and enable it to run on startup:**
```bash
sudo systemctl start ssh
sudo systemctl enable ssh
```
For CentOS or RHEL:
```bash
sudo systemctl start sshd
sudo systemctl enable sshd
```
## Verify SSH Service Status
**To ensure the OpenSSH service is running properly, check its status with:**
```bash
sudo systemctl status ssh
```
For CentOS/RHEL:
```bash
sudo systemctl status sshd
```
If the service is active, you will see an "Active: active (running)" message.
## Configure the Firewall (if applicable)
**If your machine uses a firewall (e.g., `ufw` or `firewalld`), you need to allow SSH traffic:**

For Ubuntu/Debian using `ufw`:
```bash
sudo ufw allow ssh
```
For CentOS/RHEL using `firewalld`:
```bash
sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --reload
```
## Configure SSH (Optional)
**To enhance security or customize the configuration, modify the SSH configuration file located at `/etc/ssh/sshd_config`. Common configurations   include:**

- Changing the default SSH port:
```bash
Port 2222
```
- Disabling root login:
```bash
PermitRootLogin no
```
**After making changes, restart the SSH service:**
```bash
sudo systemctl restart ssh
```
For CentOS/RHEL:
```bash
sudo systemctl restart sshd
```
For further customization or advanced configuration options, refer to the [official OpenSSH documentation.](https://www.openssh.com/manual.html)


## Test the SSH Server
**From a remote machine, test the SSH connection using the command:**
```bash
ssh your_user@server_ip_address
```
Replace `your_user` with your username and `server_ip_address` with the IP address of your server.


## Authors

- [@BrewDawg12](https://github.com/BrewDawg12)
