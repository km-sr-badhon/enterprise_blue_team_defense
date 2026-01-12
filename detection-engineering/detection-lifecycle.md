# Detection Engineering Lifecycle

## Overview
Detection engineering is a continuous, intelligence-driven process focused on identifying malicious behavior rather than static indicators. This lifecycle aligns detections with real-world attacker tradecraft and evolving enterprise environments.

This document outlines a practical detection lifecycle used in mature Blue Team and SOC operations.

---

## 1. Threat Intelligence & Attack Surface Understanding
- Analyze adversary behavior using MITRE ATT&CK
- Identify relevant threat actors targeting the organization or industry
- Understand enterprise attack surface (endpoints, identity, cloud, SaaS)

*Inputs*
- Threat intelligence reports
- Red team findings
- Incident retrospectives
- Purple team exercises

---

## 2. Detection Use Case Definition
- Define detection goals based on attacker techniques (TTPs)
- Focus on high-signal behaviors over noisy indicators
- Document assumptions, prerequisites, and expected telemetry

*Example*
- Credential dumping via LSASS access
- Suspicious OAuth application consent in cloud environments

---

## 3. Telemetry & Data Validation
- Validate required log sources exist and are reliable
- Ensure appropriate coverage across endpoint, identity, network, and cloud
- Identify blind spots and data quality issues

*Common Sources*
- EDR telemetry
- Windows Security & Sysmon logs
- Authentication and identity logs
- Cloud control plane logs

---

## 4. Detection Logic Development
- Implement detections using appropriate languages or frameworks:
  - Sigma
  - KQL
  - SPL
  - EQL
- Favor behavioral logic and correlations
- Map detections to MITRE ATT&CK techniques

---

## 5. Testing & Validation
- Test detections using:
  - Attack simulation tools
  - Red team activity
  - Purple team validation
- Measure detection fidelity and false positive rates

---

## 6. Deployment & Monitoring
- Deploy detections into production SIEM/EDR platforms
- Monitor alert volume and analyst feedback
- Track detection health and performance metrics

---

## 7. Tuning & Optimization
- Reduce false positives through context and enrichment
- Adjust thresholds and logic based on operational feedback
- Maintain documentation for tuning decisions

---

## 8. Continuous Improvement
- Retire ineffective detections
- Expand coverage based on new threats
- Regularly review ATT&CK coverage and detection gaps

---

## Conclusion
Effective detection engineering is iterative and outcome-driven. Mature Blue Teams continuously refine detections based on adversary evolution, telemetry changes, and operational lessons learned.