# Provenance

This repository is the source of record for **TrustKey**, one of the nine tools in
**Hallatec Forge**. Every published copy carries markers tying the code to this
repository and to its canonical deployment, so a fork, mirror or scrape can be
told apart from the original.

## The claim

| Property | Value |
|---|---|
| Tool | TrustKey |
| Canonical deployment | https://trustkey.hallatec.com/ |
| Source of record | https://github.com/hallatec/hallatec-trustkey |
| Suite | https://forge.hallatec.com/ |
| Copyright holder | Hallatec Technology Solutions LLC |
| Licence | AGPL-3.0-or-later |

## The markers

Provenance is asserted in four independent places, so removing one does not
erase the chain.

**1. SPDX headers.** `index.html`, `assets/hallatec.css` and
`assets/hallatec.js` each open with a machine-readable
`SPDX-License-Identifier` and `SPDX-FileCopyrightText` block naming the
copyright holder, the canonical URL and this repository. SPDX is parsed by
licence scanners such as `reuse`, FOSSA and ScanCode, so a downstream
consumer sees the origin without reading the code.

**2. Runtime object.** `assets/hallatec.js` freezes `HTC.provenance` onto
the page. Open the browser console on any deployment and run:

```js
HTC.provenance
```

A genuine deployment returns `repository: "https://github.com/hallatec/hallatec-trustkey"` and
`canonical: "https://trustkey.hallatec.com/"`. `Object.freeze` means a fork cannot quietly mutate
it at runtime without editing the source, which the AGPL then obliges them to
publish.

**3. Structured data.** The page head carries a `SoftwareSourceCode` JSON-LD
block declaring `codeRepository`, `copyrightHolder`, `license` and
`isPartOf` the Forge suite, alongside the existing `SoftwareApplication`
block. This is the form search engines and provenance crawlers read, and it is
what links the deployed page back to this repository in public indexes.

**4. Bidirectional link.** This repository names `https://trustkey.hallatec.com/` as its canonical
deployment, and that deployment names `https://github.com/hallatec/hallatec-trustkey` as its source. Either direction
alone is a claim anyone could make; the pair matching is the evidence, because
asserting the return direction requires control of the `hallatec.com` DNS zone.

## Verifying a deployment

```bash
# 1. The page declares this repository as its source
curl -s https://trustkey.hallatec.com/ | grep -A2 'code-repository'

# 2. The runtime object agrees (browser console)
#    HTC.provenance.repository === "https://github.com/hallatec/hallatec-trustkey"

# 3. The canonical link points back at the tool's own subdomain
curl -s https://trustkey.hallatec.com/ | grep 'rel="canonical"'
```

If a site serves this code without those markers, or with them rewritten to a
different owner, it is a fork rather than a Hallatec deployment. Under the
AGPL that is permitted, provided they publish their modified source and retain
the copyright notice - see `LICENSE` and `NOTICE`.

## Shared design system

`assets/hallatec.css` and `assets/hallatec.js` are common to all nine Forge
repositories. They are deliberately identical copies rather than a package
dependency, so each tool deploys standalone with no build step. A change to a
shared component must be propagated to the sibling repositories listed in
`README.md`; the SPDX header in each copy names its own repository, so it is
always clear which copy you are looking at.
