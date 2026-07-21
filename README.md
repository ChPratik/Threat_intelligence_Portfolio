# Threat Intelligence Portfolio

> **Structured vulnerability research, analysis & reporting**

This repository serves as a living portfolio of threat intelligence investigations — combining automated CVE enrichment, MITRE ATT&CK mapping, malware/IOC analysis, exploit research, and executive reporting into a single, auditable workflow.

---

## Investigations

| CVE ID | Product | Type | Severity | Status |
|--------|---------|------|----------|--------|
| [CVE-2026-45138](Investigation/CVE-2026-45138/CVE-2026-45138_REPORT.md) | CI4MS (CodeIgniter 4 CMS ERP) | Stored XSS | **MEDIUM** (CVSS 5.4) | Patched in `v0.31.9.0` |

### CVE-2026-45138 — Stored XSS in CI4MS Blog Content

**Vector:** `CVSS:3.1/AV:N/AC:L/PR:L/UI:R/S:C/C:L/I:L/A:N`  
**Weakness:** CWE-79 — Improper Neutralization of Input During Web Page Generation  
**EPSS:** 0.15% (Percentile: 4.27)  
**SSVC:** Exploitation: `PoC` / Automatable: `No` / Tech. Impact: `Partial`

The custom `html_purify` validation rule used to sanitize blog post bodies relies on by-reference mutation (`?string &$str`), but CodeIgniter 4's validator passes a **local copy** of the value — so the sanitized text is silently discarded. Blog content is written directly into the database and echoed unescaped, yielding stored XSS in any visitor's browser, including the superadmin.

**Investigation artifacts:**

| Module | File | Key Finding |
|--------|------|-------------|
| Technical Intel | [`CVE_INVESTIGATION/`](Investigation/CVE-2026-45138/CVE_INVESTIGATION/CVE-2026-45138_technical.json) | CVSS 5.4, CWE-79, PoC confirmed |
| Threat Intel | [`THREAT_INTEL_INVESTIGATION/`](Investigation/CVE-2026-45138/THREAT_INTEL_INVESTIGATION/CVE-2026-45138_threat.json) | Not in CISA KEV, no known threat actors |
| MITRE ATT&CK | [`MITRE_INVESTIGATION/`](Investigation/CVE-2026-45138/MITRE_INVESTIGATION/CVE-2026-45138_attack.json) | No techniques mapped |
| Malware Analysis | [`MALWARE_INVESTIGATION/`](Investigation/CVE-2026-45138/MALWARE_INVESTIGATION/CVE-2026-45138_malware.json) | No weaponized samples found |
| IOC Collection | [`IOC_INVESTIGATION/`](Investigation/CVE-2026-45138/IOC_INVESTIGATION/CVE-2026-45138_ioc.json) | No indicators collected |
| Exploit Research | [`EXPLOIT_INVESTIGATION/`](Investigation/CVE-2026-45138/EXPLOIT_INVESTIGATION/CVE-2026-45138_exploit.json) | No public exploit repositories |
| Executive Report | [`CVE-2026-45138_REPORT.md`](Investigation/CVE-2026-45138/CVE-2026-45138_REPORT.md) | Full risk assessment & remediation directives |

---

## Methodology

Each investigation runs through a multi-stage pipeline:

1. **CVE Intelligence** — Enrichment from NVD, CIRCL, Vulners, OpenCVE, GitHub Advisories
2. **Threat Context** — CISA KEV cross-reference, threat actor / ransomware association
3. **MITRE ATT&CK Mapping** — Technique identification, mitigation recommendations
4. **Malware & IOC Collection** — MalwareBazaar, ThreatFox, URLhaus, Pulsedive, VirusTotal
5. **Exploit Reconnaissance** — Exploit-DB, GitHub search for PoCs
6. **Analyst Review & Reporting** — SSVC scoring, executive summary, remediation directives

---

## Repository Structure

```
Threat_Intelligence_portfolio/
├── README.md                        # You are here
└── Investigation/
    └── CVE-2026-45138/
        ├── CVE-2026-45138_REPORT.md              # Executive report
        ├── CVE_INVESTIGATION/                    # Technical CVE data
        ├── EXPLOIT_INVESTIGATION/                # Exploit research
        ├── IOC_INVESTIGATION/                    # Indicators of Compromise
        ├── MALWARE_INVESTIGATION/                # Malware samples & analysis
        ├── MITRE_INVESTIGATION/                  # ATT&CK techniques
        └── THREAT_INTEL_INVESTIGATION/           # Threat actor context
```

---

## Tools & Data Sources

| Category | Sources |
|----------|---------|
| CVE Enrichment | NVD, CIRCL, Vulners, OpenCVE, OSV, Snyk, PT Security, EUVD |
| Threat Intelligence | CISA KEV, GitHub Security Advisories, AttackerKB |
| Malware Telemetry | MalwareBazaar, ThreatFox, URLhaus, Pulsedive, VirusTotal |
| Exploit Intelligence | Exploit-DB, GitHub Search |
| Frameworks | MITRE ATT&CK, SSVC, CVSS 3.1 |

---

## License

This portfolio is maintained for educational and professional demonstration purposes.
