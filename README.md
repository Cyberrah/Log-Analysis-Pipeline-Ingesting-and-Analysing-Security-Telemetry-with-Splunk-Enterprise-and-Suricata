# Security Telemetry Pipeline
### Splunk Enterprise and Suricata

**Status: In progress.** This repository currently documents the intended scope. Implementation files, test results, and investigation evidence have not yet been published.

## Objective

Build a lab pipeline that collects endpoint and network security telemetry, makes it searchable in Splunk, and supports documented SOC investigations.

## Planned workflow

1. Define the isolated lab network and log-source scope.
2. Configure Suricata monitoring and JSON event output.
3. Configure log forwarding and Splunk ingestion.
4. Validate timestamps, source types, parsing, and key fields.
5. Generate controlled lab traffic and investigate resulting events.
6. Publish searches, redacted evidence, validation results, and an investigation report.

## Planned deliverables

- Architecture and deployment documentation
- Sanitised configuration examples
- SPL searches and dashboards
- Validation records and troubleshooting notes
- Redacted screenshots and a completed SOC investigation

## Related published projects

- [Splunk SOC Home Lab](https://github.com/Cyberrah/Splunk-SOC-Home-Lab)
- [Phishing Email Analysis](https://github.com/Cyberrah/Phishing-Email-Analysis)
- [Cybersecurity portfolio](https://github.com/Cyberrah/Welcome-to-my-repository)

This is an educational lab project. Planned capabilities are not claims of completed implementation.
