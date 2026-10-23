# SSH investigation across host and network logs

## Scope

Authorised test on 16 October 2026. Client: Kali `192.168.167.4`; server: Ubuntu `192.168.167.5`; account: `cyberrah`; destination TCP port `22`. Raw host timestamps use UTC; the supplied Splunk view uses BST (UTC+1).

## Correlated connections

| Evidence | Failed connection | Successful connection |
|---|---|---|
| Client source port | `39472` | `60232` |
| Host result UTC | Failed password `20:42:47.833179` | Accepted password `20:42:56.505503` |
| Host result BST | `21:42:47.833179` | `21:42:56.505503` |
| Flow ID | `275744592746539` | `1421044264735560` |
| Flow start UTC | `20:41:28.391881` | `20:42:53.003182` |
| Flow end UTC | `20:42:48.020099` | `20:50:05.806617` |
| SSH event time BST | `21:41:28.686` | `21:42:53.054` |
| Flow record time BST | `21:43:53.195` | `21:51:14.871` |

## Method and findings

Match IP addresses, server port and client source port. Confirm that each authentication result falls between the corresponding flow start and end. Both connections meet this test. The accepted password follows the failed one by 8.672324 seconds.

The four Suricata records comprise two SSH records and two flows. They describe two connections, not four password attempts. Flow record time can be later than the connection itself, so include the delayed flow records when choosing a search window. Use **20:40–20:53 UTC** or **21:40–21:53 BST** on 16 October 2026 for these results.

Ubuntu logs prove the failed and accepted password outcomes. Suricata corroborates the connections and SSH protocol. Encrypted SSH metadata does not prove the password outcome. No alert signature is needed to perform this correlation.

The earlier timeout at 20:31:30 UTC occurred before authentication and is separate from these password outcomes. The Windows loopback test is also a separate controlled test. No malicious attack chain, brute-force campaign or compromise was established.

## Evidence

- [Ubuntu authentication records](../screenshots/ssh-host-authentication.png)
- [Suricata SSH and flow records](../screenshots/ssh-network-correlation.png)
- [Final SOC report](../reports/Kestrel_SOC_Investigation_Report.pdf)
