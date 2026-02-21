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
This lab demonstrates essential SOC analyst skills by generating, detecting, and documenting SSH authentication activity on a Linux endpoint.  
Both successful and failed SSH login attempts were intentionally triggered to create realistic authentication artifacts for analysis.  
These logs simulate attacker techniques (e.g., password guessing, invalid user enumeration) and form the foundation for SIEM alerting, brute-force detection, and incident triage workflows.

---

## Lab Objectives
- Validate baseline network connectivity from the Ubuntu VM.
- Generate SSH authentication events using both valid and invalid credentials.
- Extract SSH-specific logs using the systemd journal (`journalctl`).
- Identify failed authentication patterns and metadata.
- Map log information to SOC detection use cases.
- Capture, store, and document all evidence using professional SOC-style formatting.

---

## Environment Overview
**Target Host:** Ubuntu Linux (SSH enabled)  
**Attacker Host:** Kali Linux  
**Hypervisor:** VMware Workstation  
**Core Tools:**
- SSH client  
- `journalctl`  
- ICMP (`ping`)  
- Git + GitHub  
- Fine-grained Personal Access Token (PAT)

---

## Operational Workflow
1. Verified network connectivity:
   ```bash
   ping -c 4 8.8.8.8
