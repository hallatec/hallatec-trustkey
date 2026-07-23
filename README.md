# TrustKey

MFA and credential-hygiene coverage assessment

**Live:** [trustkey.hallatec.com](https://trustkey.hallatec.com/) · **Suite:** [Hallatec Forge](https://forge.hallatec.com/)

Part of **Hallatec Forge**, a suite of nine browser-only security tools. No
account, no upload, no server-side storage - every calculation runs locally in
your browser and nothing you type is transmitted to us.

## Running it locally

There is no build step and no dependencies. Serve the repository root with any
static file server:

```bash
python -m http.server 8080
```

Then open http://localhost:8080/.

## Deploying

This repository is a complete, self-contained Cloudflare Pages project root:

```bash
wrangler pages deploy . --project-name hallatec-trustkey --branch=main
```

Stylesheet and script use fixed filenames rather than content hashes, so bump
the `?v=` query in `index.html` whenever you change a file under
`assets/` - otherwise returning visitors keep the cached copy.

## Layout

```
index.html            the tool itself, a single page
assets/hallatec.css   shared Forge design system
assets/hallatec.js    shared component library - gauges, track meters, copy
_headers              Cloudflare Pages security headers
robots.txt            crawl directives
sitemap.xml           canonical URL for indexing
```

## Provenance

This code carries machine-readable markers - SPDX headers, a frozen
`HTC.provenance` runtime object, and `SoftwareSourceCode` JSON-LD - tying it
to this repository and to trustkey.hallatec.com. See [PROVENANCE.md](PROVENANCE.md) for how to
verify a deployment is genuine.

## The rest of the suite

| Tool | Domain | What it does |
|---|---|---|
| [Hallatec Forge Hub](https://github.com/hallatec/hallatec-forge-hub) | `forge.hallatec.com` | Suite landing page and directory for the nine Forge tools |
| [EmailGuard](https://github.com/hallatec/hallatec-emailguard) | `emailguard.hallatec.com` | Live SPF, DKIM, DMARC, BIMI and MX audit for any domain |
| [H-Score](https://github.com/hallatec/hallatec-hscore) | `hscore.hallatec.com` | Security posture score across the six NIST CSF functions |
| [AttackRank](https://github.com/hallatec/hallatec-attackrank) | `attackrank.hallatec.com` | Prioritises findings by real-world attack pressure |
| [Aegis365](https://github.com/hallatec/hallatec-aegis365) | `aegis365.hallatec.com` | Microsoft 365 hardening review across identity, email, data and device |
| [Lifeline](https://github.com/hallatec/hallatec-lifeline) | `lifeline.hallatec.com` | Backup and recovery readiness - RTO and RPO modelling |
| [Lockfall](https://github.com/hallatec/hallatec-lockfall) | `lockfall.hallatec.com` | Ransomware downtime and cost-exposure estimator |
| [CoreMap](https://github.com/hallatec/hallatec-coremap) | `coremap.hallatec.com` | Network segmentation coverage mapping |

The `assets/` design system is shared across all nine repositories as
identical copies, so each tool stays standalone and buildless. Component
changes should be propagated to the siblings above.

## Licence

[GNU AGPL-3.0-or-later](LICENSE), with an attribution term under section 7(b)
- see [LICENSE-ADDITIONAL-TERMS](LICENSE-ADDITIONAL-TERMS).

**Free to use.** Use it for any purpose including commercially, study it,
modify it, self-host it, redistribute it.

**Two conditions.** If you run a modified version **as a network service**, the
AGPL requires you to publish your modified source to that service's users. And
whether modified or not, you must **keep the copyright notice visible in the
interface** - it is the site footer, marked `data-legal-notice="required"`. You
may restyle it and add your own branding beside it; you may not remove it,
hide it, or replace it with your own.

The Hallatec name, logo marks and wordmark are trademarks and are not licensed
by the above. See [NOTICE](NOTICE).

Copyright (C) 2026 Hallatec Technology Solutions LLC
