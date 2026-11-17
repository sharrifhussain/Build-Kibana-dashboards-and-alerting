# Containment Record

- Incident ID: INC-001
- Detection Scenario: DET-001 — Brute Force Activity
- Suspicious Source IP: 192.168.1.50
- Failed Login Attempts: 5
- Successful Login Found: No

## Containment Assessment

The source IP generated five failed login attempts against the /api/login endpoint.

No successful login event was found in the available test index.

## Containment Decision

The suspicious IP has been identified and documented for temporary blocking.

Because this is a controlled lab simulation, no actual firewall rule or network block was applied.

## Notification

Security administrator notification is documented as a required response action.

## Status

Simulated containment decision documented.
