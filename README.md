# Threat Intelligence Portfolio

**Structured vulnerability research, infrastructure threat analysis & executive reporting**

A living portfolio of threat intelligence investigations combining automated CVE enrichment, MITRE ATT&CK mapping, malware/IOC analysis, exploit reconnaissance, and C-suite reporting into a single auditable workflow.

---

## Investigations

### CVEs

| CVE ID | Product | Type | Severity | Status |
|--------|---------|------|----------|--------|
| [CVE-2026-44359](Investigation/CVE/CVE-2026-44359/CVE-2026-44359_CEO_REPORT.md) | Meshtastic Firmware | Arbitrary Code Execution via CI Poisoning | **CRITICAL** (CVSS 10.0) | Patched in `v2.7.21.1370b23` |
| [CVE-2026-45138](Investigation/CVE/CVE-2026-45138/CVE-2026-45138_REPORT.md) | CI4MS (CodeIgniter 4 CMS ERP) | Stored XSS | **MEDIUM** (CVSS 5.4) | Patched in `v0.31.9.0` |

### Infrastructure Threats

| Indicator | Type | Threat Actor | Risk | Status |
|-----------|------|-------------|------|--------|
| [`morning-cell-6811.nukisora1808.workers.dev`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/morning-cell-6811.nukisora1808.workers.dev_CEO_REPORT.md) | C2 Infrastructure (Cloudflare Workers) | TA505 (suspected) | **CRITICAL** | Active — blocking & monitoring mandated |

---

### CVE-2026-44359 — Arbitrary Code Execution via CI Poisoning

| Attribute | Value |
|-----------|-------|
| **CVSS** | 10.0 — `AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:N` |
| **Weaknesses** | CWE-829 (Untrusted Control Sphere), CWE-94 (Code Generation) |
| **EPSS** | 1.00% (Percentile: 59.05) |
| **SSVC** | Exploitation: `None` / Automatable: `Yes` / Tech. Impact: `Total` |
| **Risk Rating** | High |

The Meshtastic GitHub repository's `main_matrix.yml` workflow triggers on `pull_request_target` and checks out attacker fork code with elevated `GITHUB_TOKEN` permissions — no approval gate exists. This enables **supply chain compromise**, **self-hosted runner compromise**, and **repository takeover**.

#### Artifacts

| Module | File | Key Finding |
|--------|------|-------------|
| CVE Intelligence | [`CVE_INVESTIGATION/`](Investigation/CVE/CVE-2026-44359/CVE_INVESTIGATION/CVE-2026-44359_technical.json) | CVSS 10.0, CWE-829/CWE-94, EPSS 1% |
| Threat Intel | [`THREAT_INTEL_INVESTIGATION/`](Investigation/CVE/CVE-2026-44359/THREAT_INTEL_INVESTIGATION/CVE-2026-44359_threat.json) | Not in CISA KEV, no known threat actors |
| MITRE ATT&CK | [`MITRE_INVESTIGATION/`](Investigation/CVE/CVE-2026-44359/MITRE_INVESTIGATION/CVE-2026-44359_attack.json) | T1190 (Exploit Public-Facing App), T1055 (Process Injection) — 10 mitigations |
| Malware Analysis | [`MALWARE_INVESTIGATION/`](Investigation/CVE/CVE-2026-44359/MALWARE_INVESTIGATION/CVE-2026-44359_malware.json) | No weaponized samples found |
| IOC Collection | [`IOC_INVESTIGATION/`](Investigation/CVE/CVE-2026-44359/IOC_INVESTIGATION/CVE-2026-44359_ioc.json) | No indicators collected |
| Exploit Recon | [`EXPLOIT_INVESTIGATION/`](Investigation/CVE/CVE-2026-44359/EXPLOIT_INVESTIGATION/CVE-2026-44359_exploit.json) | No public exploit repositories |
| Pipeline Output | [`FULL_REPORT_TOOL/`](Investigation/CVE/CVE-2026-44359/FULL_REPORT_TOOL/report.json) | Aggregated multi-agent report |
| Executive Report | [`CVE-2026-44359_CEO_REPORT.md`](Investigation/CVE/CVE-2026-44359/CVE-2026-44359_CEO_REPORT.md) | High-risk assessment & 6-point remediation mandate |

---

### CVE-2026-45138 — Stored XSS in CI4MS Blog Content

| Attribute | Value |
|-----------|-------|
| **CVSS** | 5.4 — `AV:N/AC:L/PR:L/UI:R/S:C/C:L/I:L/A:N` |
| **Weaknesses** | CWE-79 (Improper Neutralization — XSS) |
| **EPSS** | 0.15% (Percentile: 4.27) |
| **SSVC** | Exploitation: `PoC` / Automatable: `No` / Tech. Impact: `Partial` |
| **Risk Rating** | Medium |

The custom `html_purify` validation rule relies on by-reference mutation (`?string &$str`), but CodeIgniter 4 passes a **local copy** — sanitized text is silently discarded and raw content is stored and rendered unescaped, yielding stored XSS executable in any visitor's browser including the superadmin.

#### Artifacts

| Module | File | Key Finding |
|--------|------|-------------|
| CVE Intelligence | [`CVE_INVESTIGATION/`](Investigation/CVE/CVE-2026-45138/CVE_INVESTIGATION/CVE-2026-45138_technical.json) | CVSS 5.4, CWE-79, PoC confirmed |
| Threat Intel | [`THREAT_INTEL_INVESTIGATION/`](Investigation/CVE/CVE-2026-45138/THREAT_INTEL_INVESTIGATION/CVE-2026-45138_threat.json) | Not in CISA KEV, no known threat actors |
| MITRE ATT&CK | [`MITRE_INVESTIGATION/`](Investigation/CVE/CVE-2026-45138/MITRE_INVESTIGATION/CVE-2026-45138_attack.json) | No techniques mapped |
| Malware Analysis | [`MALWARE_INVESTIGATION/`](Investigation/CVE/CVE-2026-45138/MALWARE_INVESTIGATION/CVE-2026-45138_malware.json) | No weaponized samples found |
| IOC Collection | [`IOC_INVESTIGATION/`](Investigation/CVE/CVE-2026-45138/IOC_INVESTIGATION/CVE-2026-45138_ioc.json) | No indicators collected |
| Exploit Recon | [`EXPLOIT_INVESTIGATION/`](Investigation/CVE/CVE-2026-45138/EXPLOIT_INVESTIGATION/CVE-2026-45138_exploit.json) | No public exploit repositories |
| Pipeline Output | [`FULL_REPORT_TOOL/`](Investigation/CVE/CVE-2026-45138/FULL_REPORT_TOOL/report.json) | Aggregated multi-agent report |
| Executive Report | [`CVE-2026-45138_REPORT.md`](Investigation/CVE/CVE-2026-45138/CVE-2026-45138_REPORT.md) | Medium-risk assessment & remediation directives |

---

### Domain Intelligence: `morning-cell-6811.nukisora1808.workers.dev`

| Attribute | Value |
|-----------|-------|
| **Type** | C2 Infrastructure / Cloudflare Workers Subdomain |
| **Open Ports** | 80, 443, 2052, 2053, 2082, 2083, 2086, 2087, 2095, 2096, 8080, 8443, 8880 |
| **Suspected Actor** | TA505 (financially motivated, BEC campaigns, malware distribution) |
| **MITRE Techniques** | T1190 (Exploit Public-Facing Application), T1573 (Encrypted Channel) |
| **Risk Rating** | Critical |

A Cloudflare Workers subdomain exhibiting extensive open port exposure and encrypted channel patterns consistent with C2 infrastructure. The abuse confidence is high across all intelligence sources, with potential links to financially motivated threat actor TA505.

#### Artifacts

| Module | File | Key Finding |
|--------|------|-------------|
| C2 Intelligence | [`THREAT_INTEL_INVESTIGATION/`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/THREAT_INTEL_INVESTIGATION/morning-cell-6811.nukisora1808.workers.dev_threat.json) | CISA KEV cross-reference, no adversary context |
| MITRE ATT&CK | [`MITRE_INVESTIGATION/`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/MITRE_INVESTIGATION/morning-cell-6811.nukisora1808.workers.dev_attack.json) | T1190, T1573 — 10 mitigations |
| Malware Analysis | [`MALWARE_INVESTIGATION/`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/MALWARE_INVESTIGATION/morning-cell-6811.nukisora1808.workers.dev_malware.json) | No CVE context — indicator-only |
| IOC Collection | [`IOC_INVESTIGATION/`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/IOC_INVESTIGATION/morning-cell-6811.nukisora1808.workers.dev_ioc.json) | Open ports & C2 indicators |
| Exploit Recon | [`EXPLOIT_INVESTIGATION/`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/EXPLOIT_INVESTIGATION/morning-cell-6811.nukisora1808.workers.dev_exploit.json) | No public exploit repositories |
| Pipeline Output | [`FULL_REPORT_TOOL/`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/FULL_REPORT_TOOL/report.json) | Aggregated multi-agent report |
| Executive Report | [`morning-cell-6811.nukisora1808.workers.dev_CEO_REPORT.md`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/morning-cell-6811.nukisora1808.workers.dev_CEO_REPORT.md) | Critical-risk assessment & blocking mandate |

---

## Repository Structure

```
Threat_Intelligence_portfolio/
├── README.md
└── Investigation/
    ├── CVE/
    │   ├── CVE-2026-44359/           # Meshtastic CI Poisoning
    │   │   ├── CVE-2026-44359_CEO_REPORT.md
    │   │   ├── CVE_INVESTIGATION/
    │   │   ├── EXPLOIT_INVESTIGATION/
    │   │   ├── FULL_REPORT_TOOL/
    │   │   ├── IOC_INVESTIGATION/
    │   │   ├── MALWARE_INVESTIGATION/
    │   │   ├── MITRE_INVESTIGATION/
    │   │   └── THREAT_INTEL_INVESTIGATION/
    │   └── CVE-2026-45138/           # CI4MS Stored XSS
    │       ├── CVE-2026-45138_REPORT.md
    │       ├── CVE_INVESTIGATION/
    │       ├── EXPLOIT_INVESTIGATION/
    │       ├── FULL_REPORT_TOOL/
    │       ├── IOC_INVESTIGATION/
    │       ├── MALWARE_INVESTIGATION/
    │       ├── MITRE_INVESTIGATION/
    │       └── THREAT_INTEL_INVESTIGATION/
    └── domain/
        └── morning-cell-6811.nukisora1808.workers.dev/   # C2 Infrastructure
            ├── morning-cell-6811.nukisora1808.workers.dev_CEO_REPORT.md
            ├── EXPLOIT_INVESTIGATION/
            ├── FULL_REPORT_TOOL/
            ├── IOC_INVESTIGATION/
            ├── MALWARE_INVESTIGATION/
            ├── MITRE_INVESTIGATION/
            └── THREAT_INTEL_INVESTIGATION/
```

---

## Methodology

Each investigation executes a multi-stage pipeline:

| Stage | Agent | Sources |
|-------|-------|---------|
| 1. CVE Intelligence | `cve_intelligence` | NVD, CIRCL, Vulners, OpenCVE, GitHub Security Advisories |
| 2. Threat Context | `threat_intel` | CISA KEV catalog, threat actor / ransomware association |
| 3. MITRE ATT&CK | `attack_agent` | MITRE ATT&CK v14 — heuristic + evidence-based mapping |
| 4. Malware Telemetry | `malware_agent` | MalwareBazaar, ThreatFox, URLhaus, Pulsedive, VirusTotal |
| 5. IOC Collection | `ioc_agent` | AbuseIPDB, AlienVault OTX, Shodan, Censys |
| 6. Exploit Recon | `exploit_agent` | Exploit-DB, GitHub search |
| 7. Executive Reporting | Analyst review | SSVC v2.0.3 scoring, risk assessment, remediation directives |

---

## Data Sources

| Category | Sources |
|----------|---------|
| CVE Enrichment | NVD, CIRCL, Vulners, OpenCVE, OSV, Snyk, PT Security, EUVD |
| Threat Intelligence | CISA KEV, GitHub Security Advisories, AttackerKB |
| Malware Telemetry | MalwareBazaar, ThreatFox, URLhaus, Pulsedive, VirusTotal |
| Infrastructure Intel | Shodan, Censys, AlienVault OTX, AbuseIPDB |
| Exploit Intelligence | Exploit-DB, GitHub Search |
| Frameworks | MITRE ATT&CK v14, SSVC v2.0.3, CVSS 3.1, CWE |

---

*Maintained for educational and professional demonstration purposes.*
