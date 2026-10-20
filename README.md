# ip-as-data

Open datasets and methodology from **ip-as.net**: hosting, DNS, email infrastructure and phishing statistics derived from 310M+ domains.

> **Canonical source and latest datasets: https://ip-as.net/research/**
> This repository is a transparent, versioned mirror. The live page always has the most recent figures.

## What it measures

[ip-as.net](https://ip-as.net/) resolves tens of millions of domain names and records, for each one, the addresses it points to, the network and company that host it, its DNS and email providers, and its email security records (DMARC, SPF). The barometers built on it answer questions like *who hosts the web?*, *who runs the world's DNS and email?* and *how many popular sites protect their domain against spoofing?*

- **Domains analysed:** 310M+ (zone files, popularity lists, Certificate Transparency)
- **Sources:** ICANN CZDS, AFNIC (.fr), Internetstiftelsen (.se, .nu), Estonian Internet Foundation (.ee), [Tranco](https://tranco-list.eu/) top 1M, [Chrome UX Report](https://developer.chrome.com/docs/crux) by country, Certificate Transparency logs, public phishing blocklists; network ownership from GeoLite2 (MaxMind)
- **Aggregates only.** No zone file and no per-domain record is published here.

## Datasets

| File | Content | Live statistics |
|---|---|---|
| [`data/hosting-segments.csv`](data/hosting-segments.csv) | Hosting providers by segment (top 1M, top 10K, per country, per extension) | [/hosting/](https://ip-as.net/hosting/) |
| [`data/hosting-countries.csv`](data/hosting-countries.csv) | Main hosts for the sites most visited from each country | [/hosting/countries](https://ip-as.net/hosting/countries) |
| [`data/dns-providers.csv`](data/dns-providers.csv) | DNS provider market share, top 100K websites | [/dns/](https://ip-as.net/dns/) |
| [`data/mail-providers.csv`](data/mail-providers.csv) | Email provider market share, top 100K websites | [/mail/](https://ip-as.net/mail/) |
| [`data/email-security.csv`](data/email-security.csv) | DMARC and SPF adoption, top 100K websites | [/email-security/](https://ip-as.net/email-security/) |
| [`data/ipv6-dnssec.csv`](data/ipv6-dnssec.csv) | IPv6 and DNSSEC adoption, top 100K websites | [/ipv6-dnssec/](https://ip-as.net/ipv6-dnssec/) |
| [`data/technologies.csv`](data/technologies.csv) | Website technologies (platform, server, CDN, framework, security headers): top 100K, top 1M and most visited sites per country | [/technologies/](https://ip-as.net/technologies/) |
| [`data/phishing-by-tld.csv`](data/phishing-by-tld.csv) | Domains listed in public phishing blocklists, per extension | [/phishing/](https://ip-as.net/phishing/) |

CSV, UTF-8, comma separated, one header row. Common columns: `snapshot_date`, `sample_size` (the base the percentages are computed on), `provider`, `domains`, `share_percent`. Field definitions per file are in [`docs/methodology.md`](docs/methodology.md).

<!-- SNAPSHOT:START -->
## Latest snapshot

| File | `snapshot_date` | Rows |
|---|---|---|
| `data/hosting-segments.csv` | 2026-10-20 | 14,183 |
| `data/hosting-countries.csv` | 2026-10-20 | 1,030 |
| `data/dns-providers.csv` | 2026-10-17 | 1,260 |
| `data/mail-providers.csv` | 2026-10-17 | 444 |
| `data/email-security.csv` | 2026-10-17 | 32 |
| `data/ipv6-dnssec.csv` | 2026-10-17 | 31 |
| `data/technologies.csv` | 2026-10-19 | 25,785 |
| `data/phishing-by-tld.csv` | 2026-10-20 | 60 |
| `data/rpki-segments.csv` | 2026-10-20 | 128 |
| `data/rpki-countries.csv` | 2026-10-20 | 121 |
| `data/rpki-organisations.csv` | 2026-10-20 | 300 |
<!-- SNAPSHOT:END -->

## Main limits

- **Hosted by** = the company whose network announces the IP a name resolves to. Behind a CDN (Cloudflare, Fastly, Akamai…), that is the CDN, not the origin server.
- Counts are **domains, not sites or traffic**: parked and dormant domains count in the extension segments. Popularity segments are closer to real use.
- **.com and .net come from the full ICANN CZDS zone files** (ingested in October 2026; completed 19 October 2026). Domains are re-resolved on a rolling cycle, so individual records can be up to about three months old. Studies state the coverage they rely on.
- Popularity lists change over time: a share can move because the list moved.
- Phishing figures are **what public blocklists say**, not verified by us, and reflect an extension's size as much as its abuse handling.

Full method and limits: <https://ip-as.net/research/>.

## Licence

[Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE): use, share and adapt, including commercially, with attribution. Third-party data keeps its own terms (GeoLite2 by MaxMind; Chrome UX Report, CC BY-SA 4.0; Tranco).

## How to cite

> Poiraux, C., ip-as.net. Dataset snapshot: *date from the `snapshot_date` column*. https://ip-as.net/research/

GitHub's "Cite this repository" button uses [`CITATION.cff`](CITATION.cff). For specific statistics, please cite the corresponding dataset.

## Also available

- [JSON API](https://ip-as.net/api) (no key, [OpenAPI 3.1](https://ip-as.net/api/openapi.json)) for lookups and barometers; [`llms.txt`](https://ip-as.net/llms.txt) for AI agents.
- [Studies](https://ip-as.net/studies/) built on these datasets.

## Updates

The files are refreshed weekly from <https://ip-as.net/research/data/>; each change is a dated commit, which gives the history of the datasets. URLs on ip-as.net never carry a date.
