# Reproducing the Kestrel lab findings

This is a reproduction checklist based on the published investigation, not a new test execution or a complete automated installer. Use the [source inventory](../inventory/Kestrel_Log_Source_Inventory.xlsx), [configuration notes](../configs/README.md) and [search notes](../detections/README.md) together.

## Record the environment first

Record installed product versions, VM roles, interface names, lab addresses, timezone, clock synchronisation checks and the commit being reproduced. The documented environment has Kali as receiver, Ubuntu as the Suricata/host-log source and Windows as the event-log source. Adapt addresses to your own isolated lab.

| Gate | Check | Record before proceeding |
|---|---|---|
| Receiver | Splunk receiving destination and intended indexes exist | Receiver address, port and index names |
| Forwarding | Both forwarders can reach the receiver and read their assigned sources | Effective inputs/outputs, service identity and access checks |
| Host collection | Windows Security/System and Ubuntu auth.log/syslog arrive | Raw example, host, source, sourcetype and selected time range |
| Network collection | EVE JSON arrives and alert/SSH/flow events can be distinguished | Raw JSON, event type and extraction checks |
| Time | Source and search-display timezones are understood | UTC conversion and clock-offset observations |
| Visibility | Traffic to the monitored Ubuntu interface is observable | Interface and traffic path; do not assume all VM traffic is visible |

Use `windows`, `linux` and `suricata` for this project's documented indexes. The separate Windows starter repository uses `wineventlog`; its field assumptions are different.

## Reproduce the documented checks

| Check | Published observation | Reproduction requirement |
|---|---|---|
| Windows failed-logon detection | Six controlled failures satisfied the five-in-ten-minutes threshold | Run the [exact search](../detections/windows-five-failures.spl), verify raw XML fields and record the chosen window |
| Scheduled execution | Entries appeared after real-time bounds were replaced | Use the [documented settings](../detections/README.md); distinguish repeated evaluations from separate incidents |
| ICMP validation | Three requests produced three lab alerts | Review [the evidence](../screenshots/icmp-validation.png); the original rule text is not supplied, so a recreated rule is a new test |
| SSH correlation | One failed and one accepted password matched two network connections | Follow the [published timeline](ssh-investigation.md), matching source ports and flow intervals as well as addresses |
| Dashboard | Screenshots show authentication and network panels | Review [dashboard evidence](../screenshots/soc-dashboard.png); an original dashboard export is not supplied |

The SSH evidence window is 16 October 2026, **20:40–20:53 UTC / 21:40–21:53 BST**. Those historical searches require retained original events. Screenshots alone cannot recreate searchable telemetry. For a new run, record new times and identifiers instead of expecting the historical ones.

## Proposed checks not yet evidenced

- Compare below-threshold and at-threshold Windows test inputs.
- Verify field extraction on the actual XML quote style and on events with missing source addresses.
- Test suppression against repeated evaluations and a genuinely separate test case.
- Validate visibility for additional VM traffic paths.
- Export and re-import the original dashboard, then compare its panels.
- Record time synchronisation, retention and forwarding security settings.

## Reproduction record

For each check, record: date and timezone; software versions; repository commit; input provenance; exact query and bounds; expected result; actual result; evidence link; pass/fail/blocked; limitations and next action.

Keep newly collected evidence separate from the 16 October investigation. Do not rewrite historical observations to match a later environment.

[Project README](../README.md) · [Evidence register](evidence-register.md)
