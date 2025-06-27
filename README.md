* Setup and Use a Firewall on Linux
Objective
Configure and test basic firewall rules on a Linux system using UFW (Uncomplicated Firewall) and optionally GUFW
(Graphical UFW). Demonstrate how to allow and block traffic using ports and IPs.
Tools Used
- UFW (Uncomplicated Firewall) Command-line firewall utility
- GUFW Graphical frontend for UFW (optional)
- OS: Kali Linux
Commands Used
Enable UFW:
sudo ufw enable
Set Default Policies:
sudo ufw default deny incoming
sudo ufw default allow outgoing
Allow SSH (port 22):
sudo ufw allow 22/tcp
Allow HTTP (port 80):
sudo ufw allow 80/tcp
Block Telnet (port 23):
sudo ufw deny 23
Block a Specific IP:
sudo ufw deny from 192.168.62.128
View Rules:
sudo ufw status numbered
Delete a Rule (restore original state):
sudo ufw delete <rule-number>
GUI Configuration Steps (GUFW)
1. Install GUFW:
sudo apt install gufw -y
2. Launch:
- Terminal: sudo gufw
- Or: Applications Settings Firewall Configuration
3. Set Policies:
- Status: On
- Incoming: Deny
- Outgoing: Allow
4. Add Rules:
- Allow: SSH, HTTP
- Deny: Telnet, Blocked IPs
Testing Firewall Rules
Local Test:
sudo nc -lvp 23
# If denied: nc: Permission denied
Remote Test (from another machine):
telnet <KALI_IP> 23
# Result: Connection refused or timeout
Summary
The firewall was configured to:
- Deny all inbound traffic by default
- Allow necessary services (SSH, HTTP)
- Block insecure ports (Telnet)
- Deny traffic from specific IPs
This setup ensures a secure baseline by controlling what enters the system while allowing trusted communication.
