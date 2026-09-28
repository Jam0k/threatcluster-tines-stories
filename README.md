# ThreatCluster stories for Tines

Three importable Tines stories built on the [ThreatCluster
API](https://threatcluster.io/api). Each one is a working starting point, not a
demo: point it at your Slack, ticketing system or SIEM and it runs.

## Setup

1. Create an API key at threatcluster.io under **Settings → API & Feeds**. Every
   plan, including Free, has one.
2. In Tines, add a **Text credential** named `threatcluster` containing the key.
   The stories reference it as `{{ CREDENTIAL.threatcluster }}`, so nothing is
   hard-coded.
3. Import a story: **Stories → Import → paste the JSON**.
4. Set the schedule on the first action, and edit the last action to point at
   your own tool.

## The stories

| Story | What it does | Credits per run |
|---|---|---|
| `ransomware-sector-watch.json` | Posts to Slack when a ransomware group lists a new victim in your sector | 1 |
| `exploited-cve-triage.json` | Opens a ticket for each critical or high CVE that gained a public exploit | 1 |
| `ioc-blocklist-sync.json` | Pushes validated indicators into a firewall, proxy or SIEM lookup | 3 |

Each is scheduled so its window matches its cadence — a daily run asks for one
day of data — which keeps each listing seen once without client-side
deduplication.

## Worth knowing

- **Leak-site listings are claims, not confirmed breaches.** A group naming an
  organisation means it says it attacked them. The Slack message says so; keep
  that wording if you forward it to anyone outside the security team.
- **The IOC feed defaults to `confidence=confirmed`**, which excludes
  unreviewed indicators. Do not loosen it on a feed you block on.
- **Free keys** get 100 credits a day and read the last seven days. All three
  stories fit comfortably inside that.

## Licence

MIT for the story JSON. Data is subject to the
[ThreatCluster terms](https://threatcluster.io/terms).
