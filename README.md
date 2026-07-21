# Threat Intelligence Portfolio

**Multi-source vulnerability research, infrastructure threat analysis & executive reporting**

A structured portfolio of threat intelligence investigations combining automated CVE enrichment, MITRE ATT&CK mapping, malware telemetry, exploit reconnaissance, IOC collection, and C-suite reporting into a single auditable pipeline.

---

## Portfolio Overview

| Category | Count | Risk Range |
|----------|-------|------------|
| CVE Investigations | 6 | Medium – Critical |
| Infrastructure Threats | 1 | Critical |
| Total Artifacts | 56 | — |

---

## CVE Investigations

| CVE ID | Product | Type | CVSS | EPSS | Exec. Risk | Status |
|--------|---------|------|------|------|------------|--------|
| [CVE-2026-44359](Investigation/CVE/CVE-2026-44359/CVE-2026-44359_CEO_REPORT.md) | Meshtastic Firmware | CI Poisoning — Arbitrary Code Execution | **10.0** Critical | 1.00% | High | Patched `v2.7.21.1370b23` |
| [CVE-2026-45659](Investigation/CVE/CVE-2026-45659/CVE-2026-45659_CEO_REPORT.md) | Microsoft SharePoint | Deserialization — Remote Code Execution | **8.8** High | 3.22% | High | Open |
| [CVE-2026-56155](Investigation/CVE/CVE-2026-56155/CVE-2026-56155_CEO_REPORT.md) | Microsoft AD FS | Elevation of Privilege — Access Control | **7.8** High | 0.38% | High | Open |
| [CVE-2026-60137](Investigation/CVE/CVE-2026-60137/CVE-2026-60137_CEO_REPORT.md) | WordPress < 7.0.2 | SQL Injection — `author__not_in` WP_Query | **5.9** Medium | 4.03% | High | Patched `v7.0.2` |
| [CVE-2026-45138](Investigation/CVE/CVE-2026-45138/CVE-2026-45138_REPORT.md) | CI4MS CMS ERP | Stored XSS — Broken Validation Rule | **5.4** Medium | 0.15% | Medium | Patched `v0.31.9.0` |
| [CVE-2026-56164](Investigation/CVE/CVE-2026-56164/CVE-2026-56164_CEO_REPORT.md) | Microsoft SharePoint Server | Elevation of Privilege — Missing Auth | **5.3** Medium | 5.60% | Medium | Open |

## Infrastructure Intelligence

| Indicator | Type | Suspected Actor | Risk | Status |
|-----------|------|-----------------|------|--------|
| [`morning-cell-6811.nukisora1808.workers.dev`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/morning-cell-6811.nukisora1808.workers.dev_CEO_REPORT.md) | C2 Infrastructure — Cloudflare Workers | TA505 | **Critical** | Active — blocking mandated |

---

## Investigation Details

### CVE-2026-44359 — Critical | Meshtastic — Arbitrary Code Execution via CI Poisoning

| Attribute | Value |
|-----------|-------|
| **Vector** | `AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:N` |
| **Weaknesses** | CWE-829, CWE-94 |
| **EPSS** | 1.00% (59th percentile) |
| **SSVC** | Automatable: Yes / Exploitation: None / Tech. Impact: Total |
| **Executive Risk** | High |

The Meshtastic GitHub Actions workflow (`main_matrix.yml`) triggers on `pull_request_target` and checks out attacker fork code with elevated `GITHUB_TOKEN` permissions with no approval gate — enabling **supply chain compromise**, **self-hosted runner compromise**, and **full repository takeover**.

[Full Report](Investigation/CVE/CVE-2026-44359/CVE-2026-44359_CEO_REPORT.md)

---

### CVE-2026-45659 — High | Microsoft SharePoint — Remote Code Execution

| Attribute | Value |
|-----------|-------|
| **Vector** | `AV:N/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:H` |
| **Weaknesses** | CWE-502 (Deserialization of Untrusted Data) |
| **EPSS** | 3.22% (71st percentile) |
| **Executive Risk** | High |

Deserialization of untrusted data in Microsoft Office SharePoint allows an authorized attacker to execute code over a network.

[Full Report](Investigation/CVE/CVE-2026-45659/CVE-2026-45659_CEO_REPORT.md)

---

### CVE-2026-56155 — High | Microsoft AD FS — Elevation of Privilege

| Attribute | Value |
|-----------|-------|
| **Vector** | `AV:L/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:H` |
| **Weaknesses** | CWE-1220 (Insufficient Granularity of Access Control) |
| **EPSS** | 0.38% (37th percentile) |
| **Executive Risk** | High |

Insufficient granularity of access control in Active Directory Federation Services (AD FS) allows an authorized attacker to elevate privileges locally.

[Full Report](Investigation/CVE/CVE-2026-56155/CVE-2026-56155_CEO_REPORT.md)

---

### CVE-2026-60137 — Medium (Risk: High) | WordPress — SQL Injection

| Attribute | Value |
|-----------|-------|
| **Vector** | `AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:N/A:N` |
| **Weaknesses** | CWE-89 (SQL Injection) |
| **EPSS** | 4.03% (79th percentile) |
| **GitHub PoCs** | 10 public exploits — incl. `Icex0/wp2shell-poc` (★ 437 stars) |
| **Executive Risk** | High |

WordPress 6.8.x–7.0.x fails to sanitize the `author__not_in` parameter of `WP_Query`, enabling SQL injection when untrusted input is passed. High-quality public PoCs and elevated EPSS drive the risk rating to High despite the medium CVSS base score.

[Full Report](Investigation/CVE/CVE-2026-60137/CVE-2026-60137_CEO_REPORT.md)

---

### CVE-2026-45138 — Medium | CI4MS — Stored XSS

| Attribute | Value |
|-----------|-------|
| **Vector** | `AV:N/AC:L/PR:L/UI:R/S:C/C:L/I:L/A:N` |
| **Weaknesses** | CWE-79 (Cross-site Scripting) |
| **EPSS** | 0.15% (4th percentile) |
| **SSVC** | Automatable: No / Exploitation: PoC / Tech. Impact: Partial |
| **Executive Risk** | Medium |

The custom `html_purify` validation rule relies on by-reference mutation, but CodeIgniter 4 passes a local copy — sanitized text is discarded and raw content is stored unescaped, yielding stored XSS in any visitor's browser including the superadmin.

[Full Report](Investigation/CVE/CVE-2026-45138/CVE-2026-45138_REPORT.md)

---

### CVE-2026-56164 — Medium | Microsoft SharePoint Server — Elevation of Privilege

| Attribute | Value |
|-----------|-------|
| **Vector** | `AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:L/A:L` |
| **Weaknesses** | CWE-306 (Missing Authentication for Critical Function) |
| **EPSS** | 5.60% (84th percentile) |
| **Executive Risk** | Medium |

Missing authentication for critical function in Microsoft Office SharePoint allows an unauthorized attacker to elevate privileges over a network.

[Full Report](Investigation/CVE/CVE-2026-56164/CVE-2026-56164_CEO_REPORT.md)

---

### Domain Intelligence — Critical | C2 Infrastructure

| Attribute | Value |
|-----------|-------|
| **Indicator** | `morning-cell-6811.nukisora1808.workers.dev` |
| **Type** | Cloudflare Workers Subdomain — C2 Infrastructure |
| **Open Ports** | 80, 443, 2052, 2053, 2082, 2083, 2086, 2087, 2095, 2096, 8080, 8443, 8880 |
| **Suspected Actor** | TA505 (BEC, malware distribution) |
| **MITRE Techniques** | T1190, T1573 |

A Cloudflare Workers subdomain with extensive open port exposure and encrypted channel patterns consistent with C2 infrastructure. High abuse confidence across all intelligence sources.

[Full Report](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/morning-cell-6811.nukisora1808.workers.dev_CEO_REPORT.md)

---

## Repository Structure

```
Threat_Intelligence_portfolio/
├── README.md
└── Investigation/
    ├── CVE/
    │   ├── CVE-2026-44359/          # Meshtastic — CI Poisoning (CVSS 10.0)
    │   ├── CVE-2026-45659/          # Microsoft SharePoint — RCE (CVSS 8.8)
    │   ├── CVE-2026-56155/          # Microsoft AD FS — EoP (CVSS 7.8)
    │   ├── CVE-2026-60137/          # WordPress — SQLi (CVSS 5.9)
    │   ├── CVE-2026-45138/          # CI4MS — Stored XSS (CVSS 5.4)
    │   └── CVE-2026-56164/          # Microsoft SharePoint — EoP (CVSS 5.3)
    └── domain/
        └── morning-cell-6811.nukisora1808.workers.dev/   # C2 Infrastructure
```

Each investigation directory contains eight modules:

| Module | Description |
|--------|-------------|
| `CVE_INVESTIGATION/` | Technical CVE enrichment data (CVSS, EPSS, CWE, references) |
| `THREAT_INTEL_INVESTIGATION/` | Threat actor context, CISA KEV cross-reference |
| `MITRE_INVESTIGATION/` | MITRE ATT&CK technique mapping & mitigations |
| `MALWARE_INVESTIGATION/` | Malware telemetry (MalwareBazaar, ThreatFox, URLhaus) |
| `IOC_INVESTIGATION/` | Indicators of Compromise (Shodan, Censys, OTX) |
| `EXPLOIT_INVESTIGATION/` | Exploit reconnaissance (Exploit-DB, GitHub) |
| `FULL_REPORT_TOOL/` | Aggregated multi-agent pipeline output |
| `*_CEO_REPORT.md` | Executive report with risk assessment & remediation directives |

---

## Methodology

| # | Stage | Sources |
|---|-------|---------|
| 1 | **CVE Enrichment** | NVD, CIRCL, Vulners, OpenCVE, GitHub Security Advisories |
| 2 | **Threat Context** | CISA KEV Catalog, threat actor / ransomware association |
| 3 | **MITRE ATT&CK** | MITRE ATT&CK v14 — heuristic + evidence-based mapping |
| 4 | **Malware Telemetry** | MalwareBazaar, ThreatFox, URLhaus, Pulsedive, VirusTotal |
| 5 | **IOC Collection** | AbuseIPDB, AlienVault OTX, Shodan, Censys |
| 6 | **Exploit Recon** | Exploit-DB, GitHub public repository search |
| 7 | **Executive Reporting** | SSVC v2.0.3 scoring, risk assessment, remediation directives |

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
