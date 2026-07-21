# Threat Intelligence Portfolio

> **Structured vulnerability research, analysis & reporting**

This repository serves as a living portfolio of threat intelligence investigations — combining CVE enrichment, MITRE ATT&CK mapping, malware/IOC analysis, exploit research, and executive reporting into a single, auditable workflow.

---

## Investigations

| CVE ID | Product | Type | Severity | Status |
|--------|---------|------|----------|--------|
| [CVE-2026-44359](Investigation/CVE-2026-44359/CVE-2026-44359_CEO_REPORT.md) | Meshtastic Firmware | Arbitrary Code Execution (CI Poisoning) | **CRITICAL** (CVSS 10.0) | Patched in `v2.7.21.1370b23` |
| [CVE-2026-45138](Investigation/CVE-2026-45138/CVE-2026-45138_REPORT.md) | CI4MS (CodeIgniter 4 CMS ERP) | Stored XSS | **MEDIUM** (CVSS 5.4) | Patched in `v0.31.9.0` |

---

### CVE-2026-44359 — Critical

**Arbitrary Code Execution via `pull_request_target` Fork Checkout in Meshtastic CI Workflow**

| Attribute | Value |
|-----------|-------|
| CVSS Vector | `CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:N` |
| Weaknesses | CWE-829 (Inclusion of Functionality from Untrusted Control Sphere), CWE-94 (Improper Control of Code Generation) |
| EPSS | 1.00% (Percentile: 59.05) |
| SSVC | Exploitation: `None` / Automatable: `Yes` / Tech. Impact: `Total` |
| Risk Rating | **High** |

The Meshtastic GitHub repository's `main_matrix.yml` workflow is triggered by `pull_request_target` and multiple jobs check out the attacker's fork code and execute it with access to repository secrets and elevated `GITHUB_TOKEN` permissions — no approval gate exists. This could result in **supply chain compromise**, **self-hosted runner compromise**, and **repository takeover**.

**Investigation artifacts:**

| Module | File | Finding |
|--------|------|---------|
| Technical Intel | [`CVE_INVESTIGATION/`](Investigation/CVE-2026-44359/CVE_INVESTIGATION/CVE-2026-44359_technical.json) | CVSS 10.0, CWE-829/CWE-94, EPSS 1% |
| Threat Intel | [`THREAT_INTEL_INVESTIGATION/`](Investigation/CVE-2026-44359/THREAT_INTEL_INVESTIGATION/CVE-2026-44359_threat.json) | Not in CISA KEV, no known threat actors |
| MITRE ATT&CK | [`MITRE_INVESTIGATION/`](Investigation/CVE-2026-44359/MITRE_INVESTIGATION/CVE-2026-44359_attack.json) | T1190 (Exploit Public-Facing App), T1055 (Process Injection) — 10 mitigations |
| Malware Analysis | [`MALWARE_INVESTIGATION/`](Investigation/CVE-2026-44359/MALWARE_INVESTIGATION/CVE-2026-44359_malware.json) | No weaponized samples found |
| IOC Collection | [`IOC_INVESTIGATION/`](Investigation/CVE-2026-44359/IOC_INVESTIGATION/CVE-2026-44359_ioc.json) | No indicators collected |
| Exploit Research | [`EXPLOIT_INVESTIGATION/`](Investigation/CVE-2026-44359/EXPLOIT_INVESTIGATION/CVE-2026-44359_exploit.json) | No public exploit repositories |
| Consolidated Report | [`FULL_REPORT_TOOL/`](Investigation/CVE-2026-44359/FULL_REPORT_TOOL/report.json) | Full multi-tool pipeline output |
| Executive Report | [`CVE-2026-44359_CEO_REPORT.md`](Investigation/CVE-2026-44359/CVE-2026-44359_CEO_REPORT.md) | High-risk assessment & 6-point remediation mandate |

---

### CVE-2026-45138 — Medium

**Stored XSS in Blog Content via Broken `html_purify` Validation Rule in CI4MS**

| Attribute | Value |
|-----------|-------|
| CVSS Vector | `CVSS:3.1/AV:N/AC:L/PR:L/UI:R/S:C/C:L/I:L/A:N` |
| Weaknesses | CWE-79 (Improper Neutralization of Input During Web Page Generation) |
| EPSS | 0.15% (Percentile: 4.27) |
| SSVC | Exploitation: `PoC` / Automatable: `No` / Tech. Impact: `Partial` |
| Risk Rating | **Medium** |

The custom `html_purify` validation rule relies on by-reference mutation (`?string &$str`), but CodeIgniter 4's validator passes a **local copy** — so the sanitized text is silently discarded. Blog content is written unescaped into the database, yielding stored XSS in any visitor's browser, including the superadmin.

**Investigation artifacts:**

| Module | File | Finding |
|--------|------|---------|
| Technical Intel | [`CVE_INVESTIGATION/`](Investigation/CVE-2026-45138/CVE_INVESTIGATION/CVE-2026-45138_technical.json) | CVSS 5.4, CWE-79, PoC confirmed |
| Threat Intel | [`THREAT_INTEL_INVESTIGATION/`](Investigation/CVE-2026-45138/THREAT_INTEL_INVESTIGATION/CVE-2026-45138_threat.json) | Not in CISA KEV, no known threat actors |
| MITRE ATT&CK | [`MITRE_INVESTIGATION/`](Investigation/CVE-2026-45138/MITRE_INVESTIGATION/CVE-2026-45138_attack.json) | No techniques mapped |
| Malware Analysis | [`MALWARE_INVESTIGATION/`](Investigation/CVE-2026-45138/MALWARE_INVESTIGATION/CVE-2026-45138_malware.json) | No weaponized samples found |
| IOC Collection | [`IOC_INVESTIGATION/`](Investigation/CVE-2026-45138/IOC_INVESTIGATION/CVE-2026-45138_ioc.json) | No indicators collected |
| Exploit Research | [`EXPLOIT_INVESTIGATION/`](Investigation/CVE-2026-45138/EXPLOIT_INVESTIGATION/CVE-2026-45138_exploit.json) | No public exploit repositories |
| Consolidated Report | [`FULL_REPORT_TOOL/`](Investigation/CVE-2026-45138/FULL_REPORT_TOOL/report.json) | Full multi-tool pipeline output |
| Executive Report | [`CVE-2026-45138_REPORT.md`](Investigation/CVE-2026-45138/CVE-2026-45138_REPORT.md) | Medium-risk assessment & remediation directives |

---

## Repository Structure

```
Threat_Intelligence_portfolio/
├── README.md
└── Investigation/
    ├── CVE-2026-44359/
    │   ├── CVE-2026-44359_CEO_REPORT.md       # Executive brief (C-suite)
    │   ├── CVE_INVESTIGATION/                 # Technical CVE data
    │   ├── EXPLOIT_INVESTIGATION/             # Exploit reconnaissance
    │   ├── FULL_REPORT_TOOL/                  # Aggregated pipeline output
    │   ├── IOC_INVESTIGATION/                 # Indicators of Compromise
    │   ├── MALWARE_INVESTIGATION/             # Malware telemetry
    │   ├── MITRE_INVESTIGATION/               # ATT&CK technique mapping
    │   └── THREAT_INTEL_INVESTIGATION/        # Threat actor context
    └── CVE-2026-45138/
        ├── CVE-2026-45138_REPORT.md           # Executive report
        ├── CVE_INVESTIGATION/                 # Technical CVE data
        ├── EXPLOIT_INVESTIGATION/             # Exploit reconnaissance
        ├── FULL_REPORT_TOOL/                  # Aggregated pipeline output
        ├── IOC_INVESTIGATION/                 # Indicators of Compromise
        ├── MALWARE_INVESTIGATION/             # Malware telemetry
        ├── MITRE_INVESTIGATION/               # ATT&CK technique mapping
        └── THREAT_INTEL_INVESTIGATION/        # Threat actor context
```

---

## Methodology

Each investigation runs through a multi-stage pipeline:

| Stage | Tool/Agent | Data Sources |
|-------|-----------|--------------|
| 1. CVE Intelligence | `cve_intelligence` | NVD, CIRCL, Vulners, OpenCVE, GitHub Advisories |
| 2. Threat Context | `threat_intel` | CISA KEV catalog, Threat Actor / Ransomware association |
| 3. MITRE ATT&CK | `attack_agent` | MITRE ATT&CK framework (heuristic + evidence-based mapping) |
| 4. Malware Telemetry | `malware_agent` | MalwareBazaar, ThreatFox, URLhaus, Pulsedive, VirusTotal |
| 5. IOC Collection | `ioc_agent` | AbuseIPDB, AlienVault OTX, Shodan, Censys |
| 6. Exploit Recon | `exploit_agent` | Exploit-DB, GitHub search |
| 7. Reporting | Analyst review | SSVC scoring, executive summary, remediation directives |

---

## Tools & Data Sources

| Category | Sources |
|----------|---------|
| CVE Enrichment | NVD, CIRCL, Vulners, OpenCVE, OSV, Snyk, PT Security, EUVD |
| Threat Intelligence | CISA KEV, GitHub Security Advisories, AttackerKB |
| Malware Telemetry | MalwareBazaar, ThreatFox, URLhaus, Pulsedive, VirusTotal |
| Exploit Intelligence | Exploit-DB, GitHub Search |
| Frameworks | MITRE ATT&CK v14, SSVC v2.0.3, CVSS 3.1 |

---

## License

This portfolio is maintained for educational and professional demonstration purposes.
