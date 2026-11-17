# Lessons Learned

- Incident ID: INC-001
- Detection Scenario: DET-001 — Multiple Failed Login Attempts
- Incident Type: Controlled Brute Force Simulation

## Incident Review

Five failed login attempts from the same simulated source IP (192.168.1.50) were identified against the /api/login endpoint.

No successful login event was found in the test index.

## Detection Effectiveness

The Elasticsearch investigation query successfully identified all five failed login events.

The follow-up query found no successful login events from the same IP and endpoint.

## Root Cause

Repeated failed login attempts from a single simulated source IP.

## Detection Gaps

- The test did not include a successful login after the failed attempts.
- No real firewall blocking or account response was performed.
- Further testing is needed to validate alerting and response automation.

## Recommendations

1. Configure and test brute-force alerts in Kibana.
2. Monitor repeated failed logins from the same source IP.
3. Investigate any successful login following repeated failures.
4. Review authentication logs regularly.
5. Test containment procedures in an isolated lab environment.

## Final Status

Lessons learned documented. This controlled simulation demonstrates the incident investigation and response workflow.
