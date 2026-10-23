# Configuration examples

These are minimal, credential-free examples for the documented lab. They are not complete copies of the deployed configuration. The forwarding group name `kestrel_lab` is an illustrative name; the destination matches the demonstrated receiver.

| Example | Intended component |
|---|---|
| `windows/inputs.conf.example` | Windows Universal Forwarder inputs |
| `ubuntu/inputs.conf.example` | Ubuntu Universal Forwarder inputs |
| `forwarder/outputs.conf.example` | Forwarding destination on either Universal Forwarder |
| `receiver/inputs.conf.example` | Splunk Enterprise receiving input |

Create the `windows`, `linux` and `suricata` indexes on the receiving instance before sending data. Merge the examples into the appropriate local configuration or managed app; do not overwrite unrelated settings. The receiver example does not create indexes.

The Ubuntu service account in the lab was `splunkfwd`. Its membership in `adm` and ability to read auth.log and syslog were verified. Windows used `NT SERVICE\SplunkForwarder` with Event Log Readers access. Restarting a service may be necessary to apply configuration or updated group membership; verify its effective access afterward.

`current_only = 1` matches the supplied Windows lab input. Do not assume this is a historical backfill configuration. Retention, TLS, credential management, licence usage and production access controls were not demonstrated by these examples.

No full Suricata YAML, original custom rule text or Splunk dashboard export was supplied, so those are not reconstructed as validated configuration.
