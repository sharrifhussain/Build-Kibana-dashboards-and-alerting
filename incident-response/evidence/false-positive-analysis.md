# False Positive Analysis
## CleanCity Services

### 1. Purpose

The purpose of this analysis is to identify potential
false positives in the security detection rules and
recommend improvements to reduce unnecessary alerts.

### 2. Detection Rules Reviewed

The following detection rules were reviewed:

- DET-001: Repeated Failed Login Attempts
- DET-002: Sensitive Data Modification Request
- DET-003: Audit Event Missing Actor Identity
- Sigma: Failed Login Correlation

### 3. False Positive Scenarios

#### 3.1 DET-001 - Brute Force Detection

Detection:
- Endpoint: /api/login
- HTTP Status: 401
- Grouping: client_ip
- Threshold: 5 failed attempts

Potential False Positives:
- Legitimate users entering incorrect passwords repeatedly.
- Users forgetting their passwords.
- Automated application testing.

Investigation:
- Review source IP and timestamps.
- Check whether the user is legitimate.
- Review authentication history.
- Check for successful login events.

Recommendation:
- Correlate failed login attempts with user identity.
- Review successful logins after repeated failures.
- Apply appropriate alert thresholds.

#### 3.2 DET-002 - Tampering Detection

Detection:
- HTTP Methods: PUT, PATCH, DELETE

Potential False Positives:
- Authorized administrators updating records.
- Legitimate users modifying their information.
- Normal application workflows.
- Automated QA testing.
- Authorized maintenance activities.

Investigation:
- Identify the user and source IP.
- Review the affected endpoint.
- Check application audit logs.
- Verify whether the action was authorized.

Recommendation:
- Monitor unusual modification activity.
- Verify user permissions.
- Correlate requests with audit logs.
- Investigate unexpected DELETE requests.

#### 3.3 DET-003 - Repudiation Detection

Detection:
- Audit events missing user_id, actor or actor_id.

Potential False Positives:
- Automated background processes.
- Service accounts without user identity.
- Incomplete application logging.
- System-generated events.

Investigation:
- Identify the event source.
- Review service account activity.
- Check application logging configuration.
- Verify whether the event was expected.

Recommendation:
- Ensure audit events include actor identity.
- Configure service account identification.
- Improve application logging.
- Investigate unexplained missing identities.

### 4. Simulation Findings

Incident ID: INC-001

- Five failed login attempts were identified.
- Source IP: 192.168.1.50
- Endpoint: /api/login
- HTTP Status: 401
- No successful login event was found in the test index.

Assessment:

The controlled brute-force simulation successfully
demonstrated the identification of repeated failed
login attempts.

However, a separate legitimate-user test with
repeated incorrect passwords was not performed.
Therefore, actual false-positive frequency cannot
be determined from this simulation.

Tampering and repudiation false-positive scenarios
were identified through rule review but were not
independently simulated.

### 5. Limitations

- The analysis uses controlled sample logs.
- No production traffic was evaluated.
- Legitimate-user false-positive scenarios require
  additional testing.
- Detection performance and false-positive rates
  have not been measured.
- The JSON detection rules require validation against
  their actual Elasticsearch implementation.

### 6. Overall Recommendations

1. Review alerts before escalating incidents.
2. Correlate events with user identity and source IP.
3. Improve application audit logging.
4. Test legitimate and suspicious activity separately.
5. Tune detection thresholds using observed data.
6. Preserve investigation evidence.
7. Regularly review detection rules.

### 7. Conclusion

The reviewed detection rules cover brute-force
activity, sensitive data modification and audit
accountability gaps.

Potential false-positive scenarios have been
identified along with investigation procedures
and recommendations.

Additional testing with legitimate application
activity is required to measure actual false
positives and improve detection accuracy.

Note: This analysis is based on a controlled
laboratory environment and sample application logs.
