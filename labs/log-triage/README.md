Lab 1: Log Triage + Evidence Pack
Scenario

You are on-call. A service experienced failures and you must analyze a log file to produce an evidence pack plus a basic runbook for incident response.

Goal

Identify the most frequent failure patterns (top errors + top HTTP codes)

Capture the maximum latency observed

Produce documentation that another engineer can use to triage the same incident

Findings
Top 3 error types (count)

err_type=db → 6

err_type=auth → 5

err_type=timeout → 3

Top 3 response codes (count)

code=500 → 9

code=401 → 8

code=504 → 2

Max latency observed

2438ms

Interpretation

Most failures are driven by server errors (500) and authentication errors (401).

The presence of DB-related errors plus high max latency (2438ms) suggests backend degradation or dependency instability during the incident window.

Mini runbook (what I would do in production)

Confirm impact & scope

Validate whether error rate and latency are sustained or a short spike.

Identify which endpoints/users are affected (if available).

Triage by dominant pattern

If 401 dominates: check auth provider health, token expiration, misconfiguration, recent deployments or secrets/keys rotation.

If db errors dominate: check DB connectivity, pool saturation, timeouts, and recent schema/migration changes.

Mitigation / rollback

Apply the fastest safe mitigation (scale service, reduce load/rate-limit, disable risky feature flag if applicable).

Roll back to the last known good version if errors correlate with a recent release.

Document actions taken and outcomes.

How to reproduce (high level)

Generate or obtain a service log file (service.log) with INFO/WARN/ERROR lines.

Count occurrences by:

error type (err_type=*)

response code (code=*)

Compute:

Top 3 error types

Top 3 response codes

Maximum latency value

Save outputs as text files and keep them as an evidence pack alongside the log.

Evidence pack

All supporting outputs are stored as .txt files in this folder (counts, top errors, top codes, max latency, and inventory).
