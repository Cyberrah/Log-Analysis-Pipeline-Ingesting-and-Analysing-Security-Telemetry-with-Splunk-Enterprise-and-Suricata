# Evidence register

Supplied screenshots are copied with descriptive filenames. The report also uses pasted command output and selected XML. No original forensic export or chain-of-custody package was supplied. Screenshot names containing times refer to the supplied capture names; event times must be read from the results.

| Packaged screenshot | Source capture | What it supports |
|---|---|---|
| [Windows alerts](../screenshots/windows-triggered-alerts.png) | 16 Oct 19:01:11 | Scheduled detection entries after the settings correction |
| [Ubuntu collection](../screenshots/ubuntu-log-collection.png) | 16 Oct 19:25:40 | 165 auth.log and 5,614 syslog events in that window |
| [SOC dashboard](../screenshots/soc-dashboard.png) | 16 Oct 19:31:21 | Authentication panels and activity chart |
| [Suricata panel](../screenshots/suricata-dashboard.png) | 16 Oct 19:28:54 | ICMP and DHCP alert observations |
| [SSH host](../screenshots/ssh-host-authentication.png) | 16 Oct 21:52:50 | Failed and accepted SSH passwords |
| [SSH network](../screenshots/ssh-network-correlation.png) | 16 Oct 21:53:44 | Two SSH and two flow records |
| [Platform inventory](../screenshots/platform-source-inventory.png) | 16 Oct 19:14:07 | 63,692 events grouped into 42 combinations in that window |
| [ICMP validation](../screenshots/icmp-validation.png) | Supplied ICMP test capture | Three replies and three lab alerts |

Counts are specific to each search window. The platform combinations are index/host/source/sourcetype groups, not 42 distinct log sources. Duplicate values inside fields do not establish extra raw events.

`SHA256SUMS.txt` records hashes of the packaged files at packaging time. Those hashes support later package comparison; they are not original acquisition hashes or proof of evidence chain of custody.
