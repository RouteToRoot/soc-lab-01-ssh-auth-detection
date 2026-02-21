# SOC Lab 01 — SSH Authentication Event Detection

## 📑 Table of Contents
1. [Executive Summary](#executive-summary)
2. [Lab Objectives](#lab-objectives)
3. [Environment Overview](#environment-overview)
4. [Operational Workflow](#operational-workflow)
5. [Threat Simulation](#threat-simulation)
6. [Log Acquisition & Analysis](#log-acquisition--analysis)
7. [Detection Engineering Insights](#detection-engineering-insights)
8. [Evidence](#evidence)
9. [Conclusions](#conclusions)
10. [Next Steps](#next-steps)

---

## Executive Summary
This lab demonstrates SOC analyst fundamentals by generating and analyzing SSH authentication activity on a Linux system.  
Both **successful** and **failed** SSH login attempts were intentionally produced to simulate attacker behavior.  
These events create logs that are essential for brute-force detection, threat hunting, and SIEM correlation.

All evidence is documented and stored in the `evidence/` directory.

---

## Lab Objectives
- Validate Ubuntu network connectivity  
- Trigger SSH authentication events from a Kali host  
- Analyze SSH logs using `journalctl`  
- Identify failed login and brute-force indicators  
- Document evidence using SOC-style structure  
- Push all work to GitHub using a fine-grained PAT  

---

## Environment Overview
**Target Host:** Ubuntu Linux  
**Attacker Host:** Kali Linux  
**Hypervisor:** VMware Workstation  

**Tools Used:**
- SSH client  
- `journalctl`  
- ICMP (`ping`)  
- Git + GitHub  
- Fine-grained Personal Access Token (PAT)

---

## Operational Workflow

### 1. Connectivity Validation
Ensured the Ubuntu VM had network access using ICMP:

```bash
ping -c 4 8.8.8.8
