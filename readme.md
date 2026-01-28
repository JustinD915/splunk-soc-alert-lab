# SOC Alert & Investigation Lab (Splunk – BOTS v3)

## Overview
This project models a small Security Operations Center (SOC) workflow using Splunk and the **Boss of the SOC (BOTS) v3** dataset. The goal was to design realistic security detections, analyze alert activity, and perform structured investigations to distinguish malicious behavior from normal system noise.

The project focuses on **SIEM alerting, incident triage, and investigation documentation**, aligned with entry-level SOC analyst responsibilities.

---

## Environment & Data Sources
- **SIEM:** Splunk
- **Dataset:** BOTS v3
- **Index:** `botsv3`

Primary log sources used:
- Windows Security Events (`wineventlog:security`)
- Sysmon process telemetry (`xmlwineventlog:microsoft-windows-sysmon/operational`)
- Firewall logs (`cisco:asa`)

---

## Detections Implemented
Four scheduled alerts were created, validated, and investigated:

1. **Suspicious PowerShell EncodedCommand Execution** (High)  
   Detects PowerShell executions using encoded commands (`-enc / EncodedCommand`), commonly associated with malicious activity.

2. **New Local User Account Created** (High)  
   Monitors Windows Event ID 4720 to detect potential persistence via unauthorized account creation.

3. **Privilege Escalation – Added to Admin Group** (Critical)  
   Detects accounts added to privileged groups using Event IDs 4728 and 4732.

4. **Firewall Deny Spike Detection** (Medium)  
   Identifies abnormal spikes in firewall deny events that may indicate scanning or blocked malicious traffic.

Each alert was tested against the dataset, saved as a scheduled alert, and reviewed using returned events as investigation evidence.

---

## Investigation Process
For each alert, I:
- Validated the detection logic against real event data
- Analyzed timelines, affected hosts, and event context
- Correlated activity across multiple data sources
- Documented findings, conclusions, and recommended response actions

Investigation write-ups and screenshots are included in the `report/` directory.

---

## Skills Demonstrated
- SIEM alert creation and tuning (Splunk SPL)
- Security event analysis and log correlation
- Incident triage and investigation documentation
- Identification of persistence and privilege escalation techniques
- Translating technical findings into actionable recommendations

---

## Notes
This project is designed to reflect real-world SOC workflows rather than tool-only usage. It emphasizes **why alerts exist, what triggered them, and how an analyst would respond**, mirroring expectations for junior SOC and security analyst roles.

---

**Author:** Justin Dang  
**Date:** January 2026
