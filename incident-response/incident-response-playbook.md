# CleanCity Services — Incident Response Playbook

## 1. Purpose

This playbook defines the procedures for identifying, investigating, containing, eradicating, and recovering from security incidents detected in the CleanCity Services waste-reporting application.

## 2. Scope

This playbook covers three detection scenarios:

- DET-001: Multiple failed login attempts from the same IP address.
- DET-002: Suspicious HTTP PUT, PATCH, and DELETE requests.
- DET-003: Missing user identification in application logs.

## 3. Incident Response Process

### Phase 1: Identification and Analysis

1. Receive the security alert from Kibana.
2. Identify the alert type and severity.
3. Examine the source IP address.
4. Review timestamps and affected endpoints.
5. Check related application logs.
6. Determine whether the activity is malicious, legitimate, or inconclusive.
7. Record investigation evidence.

### Phase 2: Containment

**For DET-001 — Brute Force Activity**

1. Identify the suspicious source IP.
2. Review repeated failed login attempts.
3. Check whether a successful login followed the failures.
4. Temporarily block the suspicious IP if malicious activity is confirmed.
5. Notify the security administrator.

**For DET-002 — Suspicious HTTP Methods**

1. Identify the affected endpoint.
2. Review PUT, PATCH, and DELETE requests.
3. Verify whether the requests were authorized.
4. Restrict suspicious access if unauthorized activity is confirmed.
5. Preserve relevant logs and evidence.

**For DET-003 — Missing User Identification**

1. Identify application events with missing user identifiers.
2. Investigate the affected application component.
3. Check authentication and logging mechanisms.
4. Escalate suspicious or unexplained activity to the development team.
5. Preserve relevant audit logs.

### Phase 3: Eradication

1. Disable compromised accounts when necessary.
2. Reset affected user credentials.
3. Remove unauthorized application changes.
4. Fix identified vulnerabilities or configuration weaknesses.
5. Review access permissions.
6. Confirm that the original cause of the incident has been addressed.

### Phase 4: Recovery

1. Restore affected services and application functionality.
2. Re-enable legitimate accounts and access.
3. Verify application integrity.
4. Monitor security logs for recurring suspicious activity.
5. Confirm normal application operation.
6. Document recovery activities.

### Phase 5: Lessons Learned

1. Review the incident timeline.
2. Identify the root cause.
3. Evaluate detection effectiveness.
4. Document false positives and detection gaps.
5. Recommend improvements to security controls.

## 4. Evidence Collection

The following evidence should be retained:

- Relevant application logs.
- Source IP addresses.
- Event timestamps.
- Kibana alert screenshots.
- Investigation findings.
- Containment and recovery actions.

## 5. Incident Closure

An incident can be closed after:

- The threat has been contained.
- The root cause has been addressed.
- Recovery has been verified.
- Evidence has been documented.
- Recommendations have been recorded.

**Project:** CleanCity Services Security Monitoring and Threat Detection
