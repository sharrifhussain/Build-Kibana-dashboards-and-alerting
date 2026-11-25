# Final Security Monitoring and Incident Response Report

## CleanCity Services

**Project:** Security Monitoring and Threat Detection  
**Environment:** ELK Stack (Elasticsearch and Kibana)  
**Prepared by:** Sharrif Hussain  
**Report Type:** Final Project Report  
**Incident Reference:** INC-001

---

## 1. Executive Summary

This project focused on developing a security monitoring and threat detection solution for CleanCity Services.

The project used the ELK Stack to collect, analyze and monitor application logs. Security detection rules were developed to identify suspicious authentication activity, unauthorized data modification requests and missing audit information.

A controlled brute-force simulation was performed using sample application logs. Five failed login attempts from the same simulated source IP were identified.

No successful login event was found in the available test index.

An incident response playbook and investigation records were prepared to document containment, eradication, recovery and lessons learned.

## 2. Project Objectives

The main objectives were:

- Identify potential application security threats.
- Develop security detection rules.
- Map threats to MITRE ATT&CK.
- Build Kibana dashboards and alerts.
- Simulate a security incident.
- Document incident response procedures.
- Analyze potential false positives.
- Recommend security improvements.

## 3. Technology Stack

The following tools and technologies were used:

- Elasticsearch
- Logstash
- Kibana
- Docker
- Sigma Detection Rules
- Elasticsearch Query Language (ES|QL)
- Markdown
- Git and GitHub

## 4. Threat Detection Overview

Three major threat categories were addressed.

### 4.1 Spoofing / Brute Force

**Rule ID:** DET-001

Detection conditions:
- Endpoint: /api/login
- HTTP status: 401
- Repeated attempts from the same source IP
- Threshold: 5 attempts

**Severity:** High

**MITRE ATT&CK:** T1110 – Brute Force

### 4.2 Tampering

**Rule ID:** DET-002

Detection conditions:
- HTTP PUT requests
- HTTP PATCH requests
- HTTP DELETE requests

**Severity:** Medium

The rule identifies requests that may modify or delete application resources.

### 4.3 Repudiation

**Rule ID:** DET-003

Detection conditions:
- Audit events missing user_id.
- Missing actor.
- Missing actor_id.

**Severity:** Medium

The rule identifies audit accountability gaps.

## 5. Incident Simulation and Investigation

**Incident ID:** INC-001

**Incident Type:** Controlled Brute Force Simulation

The investigation identified:

- Source IP: 192.168.1.50
- Endpoint: /api/login
- Failed login attempts: 5
- HTTP status: 401
- Successful login events found: 0

Elasticsearch investigation queries were used to identify failed login activity and check for successful login events from the same source IP.

The available test data did not show a successful login.

## 6. Incident Response

The incident response playbook documented the following phases:

### Containment

The suspicious source IP was identified and documented for temporary blocking.

No actual firewall rule was applied because this was a controlled lab simulation.

### Eradication

No compromised account or unauthorized application change was identified in the available test data.

No credentials or application configurations were modified.

### Recovery

No production service was affected.

Lab services remained operational, and investigation evidence was preserved.

### Lessons Learned

The simulation demonstrated the importance of authentication monitoring, investigation evidence and documented response procedures.

## 7. False Positive Analysis

Potential false-positive scenarios were reviewed for all three detection categories.

**Brute Force:**
- Legitimate users entering incorrect passwords.
- Automated login testing.

**Tampering:**
- Authorized administrators updating records.
- Legitimate application workflows.
- Automated QA activities.

**Repudiation:**
- Automated background processes.
- Service accounts without user identity.
- Incomplete application logging.

These are potential false-positive scenarios, not confirmed false-positive events.

A separate legitimate-user simulation was not performed, so the actual false-positive rate could not be measured.

## 8. Security Recommendations

The following improvements are recommended for CleanCity Services:

1. Implement multi-factor authentication (MFA).
2. Monitor repeated failed login attempts.
3. Review successful logins following repeated failures.
4. Implement appropriate account lockout or rate-limiting policies.
5. Maintain detailed application audit logs.
6. Verify user permissions before sensitive data modifications.
7. Monitor unusual DELETE requests.
8. Ensure audit events include actor identity.
9. Regularly review Kibana alerts and detection rules.
10. Test incident response procedures in an isolated environment.

## 9. Project Limitations

- Testing was performed in a controlled laboratory environment.
- Sample application logs were used.
- No production systems were tested.
- No real malicious IP blocking was performed.
- Actual false-positive rates were not measured.
- Tampering and repudiation scenarios require further practical simulation.

## 10. Evidence and Documentation

The following project artifacts provide supporting evidence:

- Incident response playbook.
- Incident investigation findings.
- Incident investigation JSON.
- Containment record.
- Eradication record.
- Recovery record.
- Incident closure report.
- Lessons learned.
- False-positive analysis.
- Investigation screenshots.

## 11. Conclusion

The CleanCity Services project demonstrates a security monitoring and threat detection workflow using the ELK Stack.

The project includes threat modeling, detection rule development, security monitoring, incident investigation and documented incident response procedures.

The controlled brute-force simulation demonstrated the identification and investigation of repeated failed login attempts.

The false-positive analysis identified potential sources of unnecessary alerts and provided recommendations for improving detection accuracy.

Further testing with legitimate application activity and additional attack scenarios is recommended before considering the solution for production deployment.

**Final Project Status:** Completed as a controlled laboratory project.
