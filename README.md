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
This lab demonstrates core SOC analyst skills by generating and analyzing SSH authentication activity on a Linux host.  
By intentionally producing successful and failed SSH login attempts, we generate high-value authentication artifacts that can be used for:

- Basic intrusion detection  
- Brute-force detection tuning  
- Log correlation  
- SIEM rule development  

All evidence was captured in a controlled VMware environment and documented clearly for SOC portfolio use.

---

## Lab Objectives
- Validate network connectivity from the Ubuntu VM.  
- Generate SSH authentication events for log analysis.  
- Extract logs related to SSH using `journalctl`.  
- Identify failed authentication patterns.  
- Map observed behaviors to real SOC detection workflows.  
- Maintain proper evidence hygiene and documentation.

---

## Environment Overview
**Target Host:** Ubuntu Linux (SSH-enabled)  
**Attacker Host:** Kali Linux  
**Hypervisor:** VMware Workstation  
**Tools Used:**
- SSH client  
- `journalctl`  
- `ping`  
- Git + GitHub (evidence workflow)  
- Fine-grained PAT for authentication  

---

## Operational Workflow
1. Performed network connectivity validation from Ubuntu using ICMP.
2. Generated SSH login activity (success and failure).
3. Captured system logs via:
