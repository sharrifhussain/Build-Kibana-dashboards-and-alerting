# Incident Investigation Findings

## Incident Details
- Incident ID: INC-001
- Detection Scenario: DET-001 — Multiple Failed Login Attempts
- Incident Type: Simulated Brute Force Activity
- Source IP: 192.168.1.50
- Affected Endpoint: /api/login
- Failed Login Attempts: 5
- HTTP Status: 401

## Investigation
Five failed login attempts were identified from the same source IP address.

A follow-up Elasticsearch query checked for successful login events (HTTP 200) from the same IP address against the same endpoint.

## Finding
No successful login events were found in the test index.

## Assessment
The activity is classified as suspicious simulated brute-force activity for this lab exercise. No successful login was observed in the available test data.

## Evidence
- incident-investigation.json
- incident-investigation.png
- incident-investigation2.png
- incident-investigation3.png

## Status
Investigation completed. Proceeding to containment assessment.

Note: This is a controlled lab simulation, not a real-world security incident.
