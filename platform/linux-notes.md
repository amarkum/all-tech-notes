
# Linux Commands Guide

This guide provides essential Linux commands for managing packages, users, processes, and configuration settings across different distributions.

---

## What is Linux?

Linux is an open-source operating system that powers a large portion of today's devices, including servers, desktops, mobile devices, and embedded systems.

---

## Distributions

### Debian, Ubuntu, and Mint
- **Package Manager:** `apt`

### Red Hat, Fedora, and CentOS
- **Package Manager:** `yum`

---

## Debian, Ubuntu, and Mint Distribution Commands

1. **Install SSH**  
   Installs the OpenSSH server to enable SSH access.
   ```bash
   sudo apt install openssh-server
   ```

   **Verify if SSH service is running**
   ```bash
   sudo systemctl status ssh
   ```

   **Open SSH port in UFW (if enabled)**
   ```bash
   sudo ufw allow ssh
   ```

2. **Install Cloudera Manager**  
   Cloudera Manager can be installed via a binary file or Docker.

   - **Download and Install .bin File**
     ```bash
     wget https://archive.cloudera.com/cm6/6.3.1/cloudera-manager-installer.bin
     sudo chmod u+x cloudera-manager-installer.bin
     sudo ./cloudera-manager-installer.bin
     ```

   - **Alternative: Download Cloudera VM**
     [Cloudera VM Download](https://downloads.cloudera.com/demo_vm/virtualbox/cloudera-quickstart-vm-5.4.2-0-virtualbox.zip)

   - **Alternative: Use Docker**
     ```bash
     docker pull cloudera/quickstart:latest
     docker run --hostname=quickstart.cloudera --privileged=true -t -i -p 8888:8888 -p 80:80 cloudera/quickstart /usr/bin/docker-quickstart
     ```

3. **Uninstall Cloudera Manager**
   ```bash
   sudo sh /opt/cloudera/installer/uninstall-cloudera-manager.sh
   ```

4. **Install canberra-gtk-module**
   ```bash
   sudo apt install libcanberra-gtk-module libcanberra-gtk3-module
   ```

5. **Install GKSU**
   To use `gksudo` for graphical applications, install `gksu`.
   ```bash
   sudo apt-get install gksu
   ```

6. **SSH to root - Permission Denied**
   Modify SSH configuration to allow root login.
   ```bash
   sudo gedit /etc/ssh/sshd_config
   ```

   Change the following lines:
   ```
   PermitRootLogin yes
   # DenyUsers root
   AllowUsers root OtherUser
   ```

   **Restart SSH Service**
   ```bash
   sudo service ssh restart
   ```

7. **Failed to Detect Root Privileges - Cloudera**  
   Modify `/etc/sudoers` to allow Cloudera access without password.
   ```
   cloudera ALL=(ALL) NOPASSWD: ALL
   ```

8. **Check Directory Size**
   Lists directory sizes for specific locations.
   ```bash
   sudo du -hs /tmp /home /home/amarkum/* | sort -rh | head -10
   ```

---

## Red Hat, Fedora, and CentOS Commands

1. **Set Root Password**
   ```bash
   sudo passwd root
   ```

2. **Disable Root Account**
   ```bash
   sudo passwd -dl root
   ```

---

## SSH Commands

### Generate SSH Private and Public Keys
```bash
ssh-keygen -t rsa -f ~/.ssh/amarkum -C amarkum
```

### Add Public Key to Target Machine
Add the public key (e.g., `amarkum.pub`) to the instance for SSH access.

### SSH Login with Private Key
```bash
ssh -o StrictHostKeyChecking=no -i /Users/amarkumar/.ssh/amarkum amarkum@ip.or.hostname.com
```

---

## User Management Commands

### Add a User
```bash
useradd [Username]
```

---

## Process Management Commands

### Kill Process on a Specific Port
```bash
sudo kill -9 $(sudo lsof -t -i:80)
```

---

This guide provides a quick reference for managing Linux-based systems across major distributions, focusing on networking, user management, and software installation.
