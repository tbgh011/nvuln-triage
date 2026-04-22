# VulnTriage — AI Security Lookup

> AI-powered CVE and vulnerability triage for security and development teams. Built for the Contrast Security Hackathon 2026.

**[→ Open the app](https://tbgh011.github.io/nvuln-triage/)** · **[Quickstart Guide](https://tbgh011.github.io/nvuln-triage/quickstart.html)**

---

## What it does

VulnTriage takes a CVE ID, a Contrast Security finding, or a plain-language vulnerability description and produces a structured triage report in seconds — without having to dig through NVD advisories or raw scanner output.

Each report includes:

- **Severity & priority** — CVSS estimate, exploitability, blast radius, and fix time estimate
- **Plain-English summary** — what the vulnerability actually is, jargon-free
- **Attack scenario** — a realistic, concrete description of how an attacker would exploit it
- **Context assessment** — risk evaluated against your specific tech stack and exposure level
- **Remediation steps** — numbered, actionable, ordered by priority
- **Contrast detection notes** — how Contrast IAST, ADR, or SCA would detect or block this class of vulnerability

## Three input modes

| Mode | Use when |
|------|----------|
| **CVE Lookup** | You have a CVE ID — fetches the official description from NVD automatically, with AI fallback |
| **Contrast Finding** | You're triaging a finding from the Contrast Security dashboard |
| **Freeform** | You have pen test notes, an incident report, or any other free-text description |

## How CVE lookup works

When you hit **Fetch CVE**, the app queries the [NVD REST API](https://nvd.nist.gov/developers/vulnerabilities) directly — no API key required. This means recent CVEs (including current-year IDs) resolve correctly from the authoritative source. If NVD returns no data, the app falls back to Gemini with a clearly labelled warning to verify the result.

## Privacy & architecture

- **No backend.** The app is a single static HTML file hosted on GitHub Pages.
- **No data stored.** Nothing you enter is logged or retained anywhere.
- **Your API key goes directly from your browser to Google's Gemini API** — it never touches any other server.
- **NVD lookups** go directly from your browser to `services.nvd.nist.gov`.

## Getting started

1. Get a free Gemini API key at [aistudio.google.com/apikey](https://aistudio.google.com/apikey) — no credit card required
2. Open the [app](https://tbgh011.github.io/nvuln-triage/)
3. Paste your key into the **Google Gemini API Key** field
4. Choose a mode, enter a CVE ID or finding, add your tech stack and exposure level, and click **Analyze Vulnerability**

See the [Quickstart Guide](https://tbgh011.github.io/nvuln-triage/quickstart.html) for a full walkthrough.

## Stack

- Vanilla HTML/CSS/JS — no build step, no dependencies, no framework
- [Google Gemini 2.5 Flash](https://deepmind.google/technologies/gemini/) via the Generative Language API
- [NVD REST API v2](https://nvd.nist.gov/developers/vulnerabilities) for authoritative CVE data
- Hosted on GitHub Pages

## Local development

No build step required. Just clone and open:

```bash
git clone https://github.com/tbgh011/nvuln-triage.git
cd nvuln-triage
open index.html   # or serve with any static file server
```

To serve with Python:

```bash
python -m http.server 8080
```

Then open `http://localhost:8080` in your browser.

## Files

```
nvuln-triage/
├── index.html        # Main app
└── quickstart.html   # User guide
```

## License

MIT
