# Incident Severity Matrix & Service Level Agreements (SLAs)

**Project:** In Lap Evaluations (Chicane Works LLC)
**Purpose:** This document defines the severity levels for system incidents, integrating both user-facing support impacts and backend system metrics. It establishes internal Service Level Agreements (SLAs) for triage, response, and resolution.

---

## Severity Matrix

| Level | Classification | Impact Definition (User/Support) | System Metrics & Thresholds | Target Response SLA | Target Resolution SLA |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Sev 1** | **Critical Outage** | Complete loss of core service, widespread data loss, or severe security breach. The platform is unusable. | • API Success Rate < 90%<br>• Global P99 Latency > 5000ms (Timeouts)<br>• Database/Firebase completely unreachable<br>• Infrastructure offline | **15 Minutes** | **2 Hours** |
| **Sev 2** | **High / Severe** | A primary workflow (e.g., submitting reviews, login) is blocked for many users. No immediate workaround. | • Error rate > 5% on core endpoints (e.g., `/evaluations`, `/auth`)<br>• Core flow P99 Latency > 2000ms<br>• Third-party API integrations failing | **1 Hour** | **4 Hours** |
| **Sev 3** | **Medium / Degraded** | A feature is broken but a workaround exists, or it affects a small subset of users. System is sluggish. | • Elevated 5xx errors on non-critical paths<br>• Average Page Load > 1500ms<br>• Background job/worker queues backing up > 10 mins | **4 Hours** | **24 Hours** |
| **Sev 4** | **Low / Minor** | Minor bugs, UI glitches, or non-critical client-side issues. Core workflows function normally. | • Isolated client-side 4xx errors<br>• Negligible impact on global latency<br>• UI rendering issues on specific devices | **24 Hours** | **Next Sprint** |
| **Sev 5** | **Enhancement** | The system is operating normally. The ticket is for a new feature, cosmetic tweak, or inquiry. | • System operating within normal parameters. | **N/A** (Triage in weekly review) | **Backlog** |

---

## Metric Definitions

* **API Success Rate:** The percentage of HTTP requests returning a 2xx or 3xx status code.
* **P99 Latency:** The maximum time it takes for the fastest 99% of requests to complete. If P99 is 2000ms, 99 out of 100 users experience response times under 2 seconds.
* **Background Queues:** Time taken for asynchronous tasks (e.g., sending email notifications, generating reports) to begin processing.

## SLA Definitions

* **Target Response SLA:** The maximum amount of time between an alert triggering (or a ticket being opened) and the engineer acknowledging the issue, beginning investigation, and (if applicable) notifying users of the status.
* **Target Resolution SLA:** The target timeframe to implement a fix, deploy a patch, or establish a permanent workaround that downgrades the severity of the issue.
