# SOC Lab 01 — SSH Brute-Force Detection & Containment

## Objective
Simulate repeated SSH login failures and practice Tier 1 SOC-style detection, triage, and containment using Linux auth logs.

## Lab Environment
- Ubuntu VM (target server)
- Kali VM (attack source)
- VMware networking: (NAT/Bridged — fill in)

## Steps & Evidence
### 1) Enable SSH on Ubuntu
Commands:
- `sudo apt update`
- `sudo apt install -y openssh-server`
- `sudo systemctl enable --now ssh`

Evidence:
- Screenshot: `01-ssh-status.png`

### 2) Generate Failed Logins from Kali
Commands:
- `ssh socuser@<UBUNTU_IP>`

Evidence:
- Screenshot: `02-kali-ssh-attempt.png`

### 3) Detect in Ubuntu auth logs
Commands:
- `sudo grep "Failed password" /var/log/auth.log | tail -n 15`

Evidence:
- Screenshot: `03-failed-password-logs.png`

### 4) Contain (Block IP)
Commands:
- `sudo ufw enable`
- `sudo ufw deny from <ATTACKER_IP> to any port 22`
- `sudo ufw status numbered`

Evidence:
- Screenshot: `04-ufw-block.png`

## Findings
- Source IP (IOC): `<ATTACKER_IP>`
- Target: Ubuntu SSH (port 22)
- Result: No successful logins observed

## Remediation / Hardening (Next)
- SSH keys / disable password auth
- Fail2ban
- Restrict SSH to trusted IPs
