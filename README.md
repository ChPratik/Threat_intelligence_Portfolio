# Threat Intelligence Portfolio

**Automated vulnerability research, infrastructure threat analysis & executive reporting**

A structured portfolio of threat intelligence investigations combining multi-source CVE enrichment, MITRE ATT&CK mapping, malware telemetry, exploit reconnaissance, IOC collection, and C-suite reporting into a single auditable pipeline.

---

## Portfolio at a Glance

| Category | Count | Risk Range |
|----------|-------|------------|
| CVE Investigations | 3 | Medium – Critical |
| Infrastructure Threats | 1 | Critical |
| Total Artifacts | 32 | — |

---

## CVE Investigations

| CVE | Product | Type | CVSS | EPSS | Risk | Status |
|-----|---------|------|------|------|------|--------|
| [CVE-2026-44359](Investigation/CVE/CVE-2026-44359/CVE-2026-44359_CEO_REPORT.md) | Meshtastic Firmware | CI Poisoning — Arbitrary Code Execution | **10.0** Critical | 1.00% | **High** | Patched `v2.7.21.1370b23` |
| [CVE-2026-60137](Investigation/CVE/CVE-2026-60137/CVE-2026-60137_CEO_REPORT.md) | WordPress < 7.0.2 | Facilitated SQL Injection — `author__not_in` WP_Query | **5.9** Medium | 4.03% | **High** | Patched `v7.0.2` |
| [CVE-2026-45138](Investigation/CVE/CVE-2026-45138/CVE-2026-45138_REPORT.md) | CI4MS CMS ERP | Stored XSS — Broken `html_purify` Validation | **5.4** Medium | 0.15% | **Medium** | Patched `v0.31.9.0` |

## Infrastructure Intelligence

| Indicator | Type | Suspected Actor | Risk | Status |
|-----------|------|-----------------|------|--------|
| [`morning-cell-6811.nukisora1808.workers.dev`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/morning-cell-6811.nukisora1808.workers.dev_CEO_REPORT.md) | C2 Infrastructure — Cloudflare Workers | TA505 | **Critical** | Active — blocking mandated |

---

## Investigation Details

### CVE-2026-44359 — Critical | Arbitrary Code Execution via CI Poisoning

| Metric | Value |
|--------|-------|
| **CVSS Vector** | `AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:N` |
| **Weaknesses** | CWE-829 (Inclusion of Func. from Untrusted Control Sphere), CWE-94 (Improper Control of Code Generation) |
| **EPSS** | 1.00% (∎ 59th percentile) |
| **SSVC** | Automatable: `Yes` / Exploitation: `None` / Tech. Impact: `Total` |
| **Executive Risk** | High |

The Meshtastic GitHub Actions workflow (`main_matrix.yml`) triggers on `pull_request_target` and checks out attacker fork code with elevated `GITHUB_TOKEN` permissions. No approval gate exists, enabling **supply chain compromise**, **self-hosted runner compromise**, and **full repository takeover**.

| Artifact | Path | Key Finding |
|----------|------|-------------|
| CVE Intelligence | [`CVE_INVESTIGATION/technical.json`](Investigation/CVE/CVE-2026-44359/CVE_INVESTIGATION/CVE-2026-44359_technical.json) | CVSS 10.0, CWE-829/CWE-94, 4 references |
| Threat Intel | [`THREAT_INTEL_INVESTIGATION/threat.json`](Investigation/CVE/CVE-2026-44359/THREAT_INTEL_INVESTIGATION/CVE-2026-44359_threat.json) | Not in CISA KEV, no known threat actors |
| MITRE ATT&CK | [`MITRE_INVESTIGATION/attack.json`](Investigation/CVE/CVE-2026-44359/MITRE_INVESTIGATION/CVE-2026-44359_attack.json) | T1190, T1055 — 10 mitigations identified |
| Malware Telemetry | [`MALWARE_INVESTIGATION/malware.json`](Investigation/CVE/CVE-2026-44359/MALWARE_INVESTIGATION/CVE-2026-44359_malware.json) | No weaponized samples found |
| IOC Collection | [`IOC_INVESTIGATION/ioc.json`](Investigation/CVE/CVE-2026-44359/IOC_INVESTIGATION/CVE-2026-44359_ioc.json) | No indicators collected |
| Exploit Recon | [`EXPLOIT_INVESTIGATION/exploit.json`](Investigation/CVE/CVE-2026-44359/EXPLOIT_INVESTIGATION/CVE-2026-44359_exploit.json) | No public exploits found |
| Pipeline Output | [`FULL_REPORT_TOOL/report.json`](Investigation/CVE/CVE-2026-44359/FULL_REPORT_TOOL/report.json) | Aggregated multi-agent report |
| Executive Report | [`CEO_REPORT.md`](Investigation/CVE/CVE-2026-44359/CVE-2026-44359_CEO_REPORT.md) | High-risk assessment, 6-point remediation mandate |

---

### CVE-2026-60137 — Medium (Risk: High) | WordPress SQL Injection

| Metric | Value |
|--------|-------|
| **CVSS Vector** | `AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:N/A:N` |
| **Weaknesses** | CWE-89 (Improper Neutralization — SQL Injection) |
| **EPSS** | 4.03% (∎ 79th percentile) |
| **SSVC** | Automatable: `Yes` / Exploitation: `None` / Tech. Impact: `Total` |
| **GitHub PoCs** | 10 public exploits — incl. `Icex0/wp2shell-poc` (★ 437 stars) |
| **Executive Risk** | High |

WordPress versions 6.8.x–7.0.x fail to properly sanitize the `author__not_in` parameter of `WP_Query`, allowing SQL injection when a plugin or theme passes untrusted input. The availability of high-quality public PoCs and elevated EPSS percentile drive the risk rating to **High** despite the medium CVSS base score.

| Artifact | Path | Key Finding |
|----------|------|-------------|
| CVE Intelligence | [`CVE_INVESTIGATION/technical.json`](Investigation/CVE/CVE-2026-60137/CVE_INVESTIGATION/CVE-2026-60137_technical.json) | CVSS 5.9, CWE-89, 10 GitHub PoCs |
| Threat Intel | [`THREAT_INTEL_INVESTIGATION/threat.json`](Investigation/CVE/CVE-2026-60137/THREAT_INTEL_INVESTIGATION/CVE-2026-60137_threat.json) | Not in CISA KEV |
| MITRE ATT&CK | [`MITRE_INVESTIGATION/attack.json`](Investigation/CVE/CVE-2026-60137/MITRE_INVESTIGATION/CVE-2026-60137_attack.json) | T1055 — 2 mitigations |
| Malware Telemetry | [`MALWARE_INVESTIGATION/malware.json`](Investigation/CVE/CVE-2026-60137/MALWARE_INVESTIGATION/CVE-2026-60137_malware.json) | No weaponized samples |
| IOC Collection | [`IOC_INVESTIGATION/ioc.json`](Investigation/CVE/CVE-2026-60137/IOC_INVESTIGATION/CVE-2026-60137_ioc.json) | No indicators collected |
| Exploit Recon | [`EXPLOIT_INVESTIGATION/exploit.json`](Investigation/CVE/CVE-2026-60137/EXPLOIT_INVESTIGATION/CVE-2026-60137_exploit.json) | 10 PoCs found (highest stars: 437) |
| Pipeline Output | [`FULL_REPORT_TOOL/report.json`](Investigation/CVE/CVE-2026-60137/FULL_REPORT_TOOL/report_98377544.json) | Aggregated multi-agent report |
| Executive Report | [`CEO_REPORT.md`](Investigation/CVE/CVE-2026-60137/CVE-2026-60137_CEO_REPORT.md) | High-risk assessment, 4-point remediation mandate |

---

### CVE-2026-45138 — Medium | Stored XSS in CI4MS Blog Content

| Metric | Value |
|--------|-------|
| **CVSS Vector** | `AV:N/AC:L/PR:L/UI:R/S:C/C:L/I:L/A:N` |
| **Weaknesses** | CWE-79 (Improper Neutralization — XSS) |
| **EPSS** | 0.15% (∎ 4th percentile) |
| **SSVC** | Automatable: `No` / Exploitation: `PoC` / Tech. Impact: `Partial` |
| **Executive Risk** | Medium |

The custom `html_purify` validation rule in CI4MS relies on by-reference mutation (`?string &$str`), but CodeIgniter 4 passes a **local copy** — the sanitized text is silently discarded and raw content is stored unescaped. Stored XSS executes in any visitor's browser, including the superadmin during preview/edit.

| Artifact | Path | Key Finding |
|----------|------|-------------|
| CVE Intelligence | [`CVE_INVESTIGATION/technical.json`](Investigation/CVE/CVE-2026-45138/CVE_INVESTIGATION/CVE-2026-45138_technical.json) | CVSS 5.4, CWE-79, PoC confirmed |
| Threat Intel | [`THREAT_INTEL_INVESTIGATION/threat.json`](Investigation/CVE/CVE-2026-45138/THREAT_INTEL_INVESTIGATION/CVE-2026-45138_threat.json) | Not in CISA KEV, no known threat actors |
| MITRE ATT&CK | [`MITRE_INVESTIGATION/attack.json`](Investigation/CVE/CVE-2026-45138/MITRE_INVESTIGATION/CVE-2026-45138_attack.json) | No techniques mapped |
| Malware Telemetry | [`MALWARE_INVESTIGATION/malware.json`](Investigation/CVE/CVE-2026-45138/MALWARE_INVESTIGATION/CVE-2026-45138_malware.json) | No weaponized samples |
| IOC Collection | [`IOC_INVESTIGATION/ioc.json`](Investigation/CVE/CVE-2026-45138/IOC_INVESTIGATION/CVE-2026-45138_ioc.json) | No indicators collected |
| Exploit Recon | [`EXPLOIT_INVESTIGATION/exploit.json`](Investigation/CVE/CVE-2026-45138/EXPLOIT_INVESTIGATION/CVE-2026-45138_exploit.json) | No public exploits found |
| Pipeline Output | [`FULL_REPORT_TOOL/report.json`](Investigation/CVE/CVE-2026-45138/FULL_REPORT_TOOL/report.json) | Aggregated multi-agent report |
| Executive Report | [`REPORT.md`](Investigation/CVE/CVE-2026-45138/CVE-2026-45138_REPORT.md) | Medium-risk assessment, remediation directives |

---

### Domain: `morning-cell-6811.nukisora1808.workers.dev` — Critical | C2 Infrastructure

| Metric | Value |
|--------|-------|
| **Type** | Cloudflare Workers Subdomain — C2 Infrastructure |
| **Open Ports** | 80, 443, 2052, 2053, 2082, 2083, 2086, 2087, 2095, 2096, 8080, 8443, 8880 |
| **Suspected Actor** | TA505 (financially motivated — BEC, malware distribution) |
| **MITRE Techniques** | T1190 (Exploit Public-Facing App), T1573 (Encrypted Channel) |
| **Executive Risk** | Critical |

A Cloudflare Workers subdomain exhibiting extensive open port exposure and encrypted channel patterns consistent with C2 infrastructure. High abuse confidence across all intelligence sources.

| Artifact | Path | Key Finding |
|----------|------|-------------|
| Threat Intel | [`THREAT_INTEL_INVESTIGATION/threat.json`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/THREAT_INTEL_INVESTIGATION/morning-cell-6811.nukisora1808.workers.dev_threat.json) | CISA KEV cross-reference |
| MITRE ATT&CK | [`MITRE_INVESTIGATION/attack.json`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/MITRE_INVESTIGATION/morning-cell-6811.nukisora1808.workers.dev_attack.json) | T1190, T1573 — 10 mitigations |
| Malware Telemetry | [`MALWARE_INVESTIGATION/malware.json`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/MALWARE_INVESTIGATION/morning-cell-6811.nukisora1808.workers.dev_malware.json) | Indicator-only (no CVE context) |
| IOC Collection | [`IOC_INVESTIGATION/ioc.json`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/IOC_INVESTIGATION/morning-cell-6811.nukisora1808.workers.dev_ioc.json) | Open ports & C2 indicators |
| Exploit Recon | [`EXPLOIT_INVESTIGATION/exploit.json`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/EXPLOIT_INVESTIGATION/morning-cell-6811.nukisora1808.workers.dev_exploit.json) | No public exploits |
| Pipeline Output | [`FULL_REPORT_TOOL/report.json`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/FULL_REPORT_TOOL/report.json) | Aggregated multi-agent report |
| Executive Report | [`CEO_REPORT.md`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/morning-cell-6811.nukisora1808.workers.dev_CEO_REPORT.md) | Critical-risk assessment, blocking & monitoring mandate |

---

## Repository Structure

```
Threat_Intelligence_portfolio/
├── README.md
└── Investigation/
    ├── CVE/
    │   ├── CVE-2026-44359/          # Meshtastic — CI Poisoning (Critical)
    │   │   ├── CEO_REPORT.md
    │   │   ├── CVE_INVESTIGATION/
    │   │   ├── EXPLOIT_INVESTIGATION/
    │   │   ├── FULL_REPORT_TOOL/
    │   │   ├── IOC_INVESTIGATION/
    │   │   ├── MALWARE_INVESTIGATION/
    │   │   ├── MITRE_INVESTIGATION/
    │   │   └── THREAT_INTEL_INVESTIGATION/
    │   ├── CVE-2026-60137/          # WordPress — SQL Injection (High Risk)
    │   │   ├── CEO_REPORT.md
    │   │   ├── CVE_INVESTIGATION/
    │   │   ├── EXPLOIT_INVESTIGATION/
    │   │   ├── FULL_REPORT_TOOL/
    │   │   ├── IOC_INVESTIGATION/
    │   │   ├── MALWARE_INVESTIGATION/
    │   │   ├── MITRE_INVESTIGATION/
    │   │   └── THREAT_INTEL_INVESTIGATION/
    │   └── CVE-2026-45138/          # CI4MS — Stored XSS (Medium)
    │       ├── REPORT.md
    │       ├── CVE_INVESTIGATION/
    │       ├── EXPLOIT_INVESTIGATION/
    │       ├── FULL_REPORT_TOOL/
    │       ├── IOC_INVESTIGATION/
    │       ├── MALWARE_INVESTIGATION/
    │       ├── MITRE_INVESTIGATION/
    │       └── THREAT_INTEL_INVESTIGATION/
    └── domain/
        └── morning-cell-6811.nukisora1808.workers.dev/   # C2 Infrastructure (Critical)
            ├── CEO_REPORT.md
            ├── EXPLOIT_INVESTIGATION/
            ├── FULL_REPORT_TOOL/
            ├── IOC_INVESTIGATION/
            ├── MALWARE_INVESTIGATION/
            ├── MITRE_INVESTIGATION/
            └── THREAT_INTEL_INVESTIGATION/
```

---

## Methodology

Each investigation executes a multi-agent pipeline with the following stages:

| # | Stage | Agent | Intelligence Sources |
|---|-------|-------|---------------------|
| 1 | **CVE Enrichment** | `cve_intelligence` | NVD, CIRCL, Vulners, OpenCVE, GitHub Security Advisories |
| 2 | **Threat Context** | `threat_intel` | CISA KEV Catalog, Threat Actor / Ransomware Association |
| 3 | **MITRE ATT&CK** | `attack_agent` | MITRE ATT&CK v14 — Heuristic + Evidence-Based Mapping |
| 4 | **Malware Telemetry** | `malware_agent` | MalwareBazaar, ThreatFox, URLhaus, Pulsedive, VirusTotal |
| 5 | **IOC Collection** | `ioc_agent` | AbuseIPDB, AlienVault OTX, Shodan, Censys |
| 6 | **Exploit Recon** | `exploit_agent` | Exploit-DB, GitHub Public Repository Search |
| 7 | **Reporting** | Analyst Review | SSVC v2.0.3 Scoring, Risk Assessment, Remediation Directives |

---

## Intelligence Sources

| Category | Sources |
|----------|---------|
| **CVE Enrichment** | NVD, CIRCL, Vulners, OpenCVE, OSV, Snyk, PT Security, EUVD |
| **Threat Intelligence** | CISA KEV, GitHub Security Advisories, AttackerKB |
| **Malware Telemetry** | MalwareBazaar, ThreatFox, URLhaus, Pulsedive, VirusTotal |
| **Infrastructure Intel** | Shodan, Censys, AlienVault OTX, AbuseIPDB |
| **Exploit Intelligence** | Exploit-DB, GitHub Search |
| **Frameworks** | MITRE ATT&CK v14, SSVC v2.0.3, CVSS 3.1, CWE |

---

*Maintained for educational and professional demonstration purposes.*
