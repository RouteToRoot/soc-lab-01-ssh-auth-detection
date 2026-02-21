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
9. [Completion Status](#completion-status)  
10. [Next Steps](#next-steps)

---

## Executive Summary
This lab demonstrates foundational SOC analyst competencies by generating, identifying, and analyzing SSH authentication events on a Linux host.  
The activity simulates attacker behavior (failed SSH login attempts) and uses native system logs to validate detection capabilities.  
Captured log evidence is stored in a structured repository layout to support future SIEM integration or portfolio review.

---

## Lab Objectives
- Validate baseline network connectivity from the Ubuntu VM.
- Generate SSH authentication activity (successful and failed).
- Collect system logs from the `sshd` service.
- Interpret and classify SSH authentication events.
- Identify indicators related to brute-force activity or unauthorized access.
- Document findings using SOC-style reporting structure.

---

## Environment Overview
**Target System:** Ubuntu Linux  
**Attacker System:** Kali Linux  
**Hypervisor:** VMware Workstation  
**Core Tools:**
- SSH client  
- systemd journal (`journalctl`)  
- Ping (ICMP testing)  
- Git + GitHub  
- Fine-grained Personal Access Token (PAT) for Git push authentication  

---

## Operational Workflow
The lab consists of the following major phases:

1. **Connectivity Validation:**  
   Confirming that the Ubuntu VM was reachable using ICMP (`ping`).

2. **Event Generation:**  
   Triggering both valid and invalid SSH authentication attempts from the Kali VM.

3. **Log Retrieval:**  
   Using `journalctl -u ssh` to retrieve authentication events logged by systemd.

4. **Evidence Capture:**  
   Storing screenshots documenting each activity and placing them into the `evidence/` folder.

5. **Repository Update:**  
   Committing and pushing all artifacts to GitHub using a fine-grained PAT.

---

## Threat Simulation
A controlled SSH authentication sequence was executed to replicate attacker behavior.  
This included:

- Attempts using **incorrect credentials** to simulate brute-force behavior.  
- A **successful SSH login** to capture normal authentication entries.  

These events helped generate a diverse log sample suitable for analysis.

---

## Log Acquisition & Analysis

### Commands Executed
#### Connectivity Test
