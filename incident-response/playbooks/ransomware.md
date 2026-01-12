# Incident Response Playbook: Ransomware

## Overview
This playbook provides a structured, practical approach for responding to ransomware incidents in enterprise environments.  
It is designed to support SOC analysts, incident responders, and DFIR teams during high-pressure situations where speed, accuracy, and coordination are critical.

The focus is on *containment first*, followed by *eradication, recovery*, and **lessons learned**—not on attribution or ransom negotiation.

---

## Objectives
- Rapidly identify ransomware activity
- Contain spread and limit business impact
- Preserve forensic evidence
- Support safe system recovery
- Feed lessons learned back into detections and controls

---

## 1. Identification

### Common Indicators
- Ransom notes present on endpoints or servers
- Sudden mass file encryption or file extension changes
- Unusual file rename or delete operations
- EDR alerts indicating ransomware-like behavior
- Disabled security tools or tampered backups
- Spikes in CPU, disk, or I/O activity on endpoints

### Initial Triage Questions
- Which systems are affected?
- Is the activity ongoing?
- Are critical systems (AD, backups, file servers) impacted?
- Is there evidence of lateral movement?

---

## 2. Containment

### Immediate Actions
- Isolate affected endpoints from the network (EDR or network-level)
- Disable compromised user accounts
- Block identified malicious hashes, domains, and IPs
- Suspend scheduled tasks or scripts linked to the attack

### Network-Level Controls
- Restrict SMB/RDP traffic where possible
- Monitor east-west traffic for spread indicators
- Preserve firewall and proxy logs

⚠️ Avoid shutting down systems unless encryption is actively spreading and isolation is not possible.


---

## 3. Eradication

### Investigation Focus
- Identify initial access vector (phishing, RDP, exploit, supply chain)
- Locate persistence mechanisms:
  - Scheduled tasks
  - Services
  - Registry run keys
- Identify privilege escalation and credential access activity

### Remediation
- Remove malware, scripts, and persistence artifacts
- Reset credentials for affected users and admins
- Patch exploited vulnerabilities
- Validate integrity of security tooling

---

## 4. Recovery

### System Restoration
- Restore systems from known-good backups
- Validate backups before restoration
- Monitor restored systems for re-infection indicators

### Validation
- Confirm no active C2 communication
- Validate endpoint and server behavior post-recovery
- Monitor for repeat encryption attempts

Ransom payment is a business decision and falls outside the scope of this playbook.


---

## 5. Post-Incident Actions

### Lessons Learned
- What detections failed or triggered late?
- Were lateral movement indicators missed?
- Were backups adequately protected?

### Detection & Control Improvements
- Create or tune ransomware-related detections
- Improve logging coverage
- Update IR runbooks and escalation paths

### Reporting
- Document timeline of events
- Capture attacker techniques mapped to MITRE ATT&CK
- Provide executive-level summary of impact and response

---

## References
- MITRE ATT&CK – Ransomware Techniques
- NIST SP 800-61: Incident Handling Guide
- Internal SOC and DFIR procedures