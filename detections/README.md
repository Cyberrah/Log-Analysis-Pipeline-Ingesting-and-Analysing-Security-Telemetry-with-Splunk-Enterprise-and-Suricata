# Detection and investigation searches

These searches accompany the validated lab evidence. They are not a claim of testing on other Splunk installations. Confirm index names, timezone and field extraction before reuse.

- `windows-five-failures.spl`: scheduled detection with a ten-minute lookback and a five-failure threshold.
- `windows-failures-by-account.spl`: failed logon dashboard table, without the alert threshold.
- `ssh-host-authentication.spl`: SSH password outcomes from the Ubuntu log. Set an absolute investigation window in the time picker.
- `ssh-network-correlation.spl`: SSH and flow records for the two lab hosts. Set the same absolute window, allowing for delayed flow emission.
- `suricata-alerts.spl`: signatures and rule severities from alert events only.
- `log-source-inventory.spl`: source inventory over the chosen 24-hour period.
- `ubuntu-log-collection.spl`: counts and last seen time by Ubuntu source.

## Windows alert settings

Type: Scheduled. Cron: `* * * * *`. Earliest: `-10m`. Latest: `now`. Number of results greater than `0`. Trigger once per evaluation. Action: Add to Triggered Alerts, Medium severity.

The SPL threshold already removes groups with fewer than five failures. Setting the UI threshold to greater than five result rows would change the intended detection. Overlapping windows may produce repeated alerts; test throttling by `host`, `user` and `src_ip` before broader use.

## Field extraction

Windows regexes match the single-quoted XML format in the supplied evidence. Suricata searches use `spath` for JSON; where existing extraction already works, validate whether this causes duplicate field values. Do not count repeated values inside one multivalue field as additional raw events.

The dashboard export was not supplied. These are selected reusable searches, not a complete dashboard definition or an automated installer.
