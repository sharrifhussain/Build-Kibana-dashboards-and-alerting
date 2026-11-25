# Incident Response Playbook
## CleanCity Services

### 1. Purpose
This playbook defines the steps for identifying,
investigating, containing, eradicating and recovering
from security incidents.

### 2. Scope
This playbook covers:
- Spoofing and Brute Force attacks
- Unauthorized data modification (Tampering)
- Missing audit information (Repudiation)

### 3. Incident Detection
Security alerts are identified through:
- Elasticsearch detection rules
- Kibana dashboards and alerts
- Application logs

### 4. Initial Investigation
1. Record the alert ID.
2. Record the incident timestamp.
3. Identify the source IP address.
4. Review related application logs.
5. Determine the severity.
6. Preserve investigation evidence.

### 5. Containment
1. Identify affected systems and accounts.
2. Restrict confirmed malicious access.
3. Block malicious IPs if authorized.
4. Preserve relevant logs and evidence.

### 6. Eradication
1. Identify the root cause.
2. Remove unauthorized access.
3. Reset compromised credentials.
4. Fix vulnerable configurations.
5. Verify that the threat is removed.

### 7. Recovery
1. Restore affected services.
2. Verify application functionality.
3. Monitor authentication and application logs.
4. Confirm normal operations.

### 8. Lessons Learned
1. Document incident findings.
2. Identify detection gaps.
3. Review false positives.
4. Recommend security improvements.
5. Update detection rules and procedures.
