<p align="center">
  <img src="https://img.shields.io/badge/Status-Active-00ADD8?style=for-the-badge&logo=virustotal&logoColor=white"/>
  <img src="https://img.shields.io/badge/Investigations-7-9146FF?style=for-the-badge&logo=bookstack&logoColor=white"/>
  <img src="https://img.shields.io/badge/Artifacts-56-00B368?style=for-the-badge&logo=files&logoColor=white"/>
  <img src="https://img.shields.io/badge/Risk_Range-Medium_–_Critical-FF4500?style=for-the-badge&logo=securitas&logoColor=white"/>
</p>

<h1 align="center">🛡️ Threat Intelligence Portfolio</h1>
<p align="center"><b>Multi-source vulnerability research · Infrastructure threat analysis · Executive reporting</b></p>
<p align="center">Automated CVE enrichment · MITRE ATT&CK mapping · Malware telemetry · Exploit recon · IOC collection</p>

<br>

---

## 📊 Dashboard

| Metric | Count |
|--------|:-----:|
| <img src="https://img.shields.io/badge/-CRITICAL-FF0000?style=flat-square"/> Critical CVEs | 1 |
| <img src="https://img.shields.io/badge/-HIGH-FF8C00?style=flat-square"/> High Risk Investigations | 4 |
| <img src="https://img.shields.io/badge/-MEDIUM-FFD700?style=flat-square"/> Medium Risk Investigations | 2 |
| <img src="https://img.shields.io/badge/-Infrastructure-8A2BE2?style=flat-square"/> Infrastructure Threats | 1 |
| **Total Investigations** | **7** |

---

## 🔬 CVE Investigations

| CVE ID | Product | Type | CVSS | EPSS | Risk | Status |
|--------|---------|------|:----:|:----:|:----:|--------|
| [CVE-2026-44359](Investigation/CVE/CVE-2026-44359/CVE-2026-44359_CEO_REPORT.md) | Meshtastic Firmware | CI Poisoning — Arbitrary Code Execution | <img src="https://img.shields.io/badge/10.0-CRITICAL-FF0000?style=flat-square"/> | <img src="https://img.shields.io/badge/1.00%25-59th-FF8C00?style=flat-square"/> | <img src="https://img.shields.io/badge/HIGH-FF8C00?style=flat-square"/> | ✅ Patched `v2.7.21.1370b23` |
| [CVE-2026-45659](Investigation/CVE/CVE-2026-45659/CVE-2026-45659_CEO_REPORT.md) | Microsoft SharePoint | Deserialization — Remote Code Execution | <img src="https://img.shields.io/badge/8.8-HIGH-FF8C00?style=flat-square"/> | <img src="https://img.shields.io/badge/3.22%25-71st-FF8C00?style=flat-square"/> | <img src="https://img.shields.io/badge/HIGH-FF8C00?style=flat-square"/> | 🔴 Open |
| [CVE-2026-56155](Investigation/CVE/CVE-2026-56155/CVE-2026-56155_CEO_REPORT.md) | Microsoft AD FS | Elevation of Privilege — Access Control | <img src="https://img.shields.io/badge/7.8-HIGH-FF8C00?style=flat-square"/> | <img src="https://img.shields.io/badge/0.38%25-37th-9ACD32?style=flat-square"/> | <img src="https://img.shields.io/badge/HIGH-FF8C00?style=flat-square"/> | 🔴 Open |
| [CVE-2026-60137](Investigation/CVE/CVE-2026-60137/CVE-2026-60137_CEO_REPORT.md) | WordPress < 7.0.2 | SQL Injection — WP_Query | <img src="https://img.shields.io/badge/5.9-MEDIUM-FFD700?style=flat-square"/> | <img src="https://img.shields.io/badge/4.03%25-79th-FF8C00?style=flat-square"/> | <img src="https://img.shields.io/badge/HIGH-FF8C00?style=flat-square"/> | ✅ Patched `v7.0.2` |
| [CVE-2026-45138](Investigation/CVE/CVE-2026-45138/CVE-2026-45138_REPORT.md) | CI4MS CMS ERP | Stored XSS — Validation Bypass | <img src="https://img.shields.io/badge/5.4-MEDIUM-FFD700?style=flat-square"/> | <img src="https://img.shields.io/badge/0.15%25-4th-9ACD32?style=flat-square"/> | <img src="https://img.shields.io/badge/MEDIUM-FFD700?style=flat-square"/> | ✅ Patched `v0.31.9.0` |
| [CVE-2026-56164](Investigation/CVE/CVE-2026-56164/CVE-2026-56164_CEO_REPORT.md) | Microsoft SharePoint Server | Elevation of Privilege — Missing Auth | <img src="https://img.shields.io/badge/5.3-MEDIUM-FFD700?style=flat-square"/> | <img src="https://img.shields.io/badge/5.60%25-84th-FF8C00?style=flat-square"/> | <img src="https://img.shields.io/badge/MEDIUM-FFD700?style=flat-square"/> | 🔴 Open |

## 🌐 Infrastructure Intelligence

| Indicator | Type | Actor | Risk | Status |
|-----------|------|-------|:----:|--------|
| [`morning-cell-6811.nukisora1808.workers.dev`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/morning-cell-6811.nukisora1808.workers.dev_CEO_REPORT.md) | C2 — Cloudflare Workers | TA505 | <img src="https://img.shields.io/badge/CRITICAL-FF0000?style=flat-square"/> | 🟢 Active — blocking mandated |

---

## 📋 Deep Dive

<details>
<summary><b>CVE-2026-44359</b> — 🔴 Arbitrary Code Execution via CI Poisoning <img src="https://img.shields.io/badge/CRITICAL-FF0000?style=flat-square"/> <img src="https://img.shields.io/badge/Risk-HIGH-FF8C00?style=flat-square"/></summary>
<br>

| Metric | Value |
|--------|-------|
| **CVSS Vector** | `AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:N` |
| **Weaknesses** | CWE-829 · CWE-94 |
| **EPSS** | 1.00% (∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎ 59th percentile) |
| **SSVC** | Automatable: `Yes` / Exploitation: `None` / Tech. Impact: `Total` |

**Summary:** Meshtastic's `main_matrix.yml` workflow triggers on `pull_request_target` and checks out attacker fork code with elevated `GITHUB_TOKEN` — no approval gate. Enables supply chain compromise and repository takeover.

**Artifacts:**

| Module | Key Finding |
|--------|-------------|
| `CVE_INVESTIGATION/` | CVSS 10.0, CWE-829/CWE-94, 4 references |
| `THREAT_INTEL_INVESTIGATION/` | Not in CISA KEV, no known threat actors |
| `MITRE_INVESTIGATION/` | T1190, T1055 — 10 mitigations |
| `MALWARE_INVESTIGATION/` | No weaponized samples found |
| `IOC_INVESTIGATION/` | No indicators collected |
| `EXPLOIT_INVESTIGATION/` | No public exploits found |
| `FULL_REPORT_TOOL/` | Aggregated multi-agent report |

➡️ [Executive Report](Investigation/CVE/CVE-2026-44359/CVE-2026-44359_CEO_REPORT.md)

</details>

<details>
<summary><b>CVE-2026-45659</b> — 🔴 Microsoft SharePoint Remote Code Execution <img src="https://img.shields.io/badge/HIGH-FF8C00?style=flat-square"/> <img src="https://img.shields.io/badge/Risk-HIGH-FF8C00?style=flat-square"/></summary>
<br>

| Metric | Value |
|--------|-------|
| **CVSS Vector** | `AV:N/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:H` |
| **Weaknesses** | CWE-502 (Deserialization of Untrusted Data) |
| **EPSS** | 3.22% (∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎ 71st percentile) |
| **Executive Risk** | High |

**Summary:** Deserialization of untrusted data in Microsoft Office SharePoint allows an authorized attacker to execute code over a network.

➡️ [Executive Report](Investigation/CVE/CVE-2026-45659/CVE-2026-45659_CEO_REPORT.md)

</details>

<details>
<summary><b>CVE-2026-56155</b> — 🔴 Microsoft AD FS Elevation of Privilege <img src="https://img.shields.io/badge/HIGH-FF8C00?style=flat-square"/> <img src="https://img.shields.io/badge/Risk-HIGH-FF8C00?style=flat-square"/></summary>
<br>

| Metric | Value |
|--------|-------|
| **CVSS Vector** | `AV:L/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:H` |
| **Weaknesses** | CWE-1220 (Insufficient Granularity of Access Control) |
| **EPSS** | 0.38% (∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎ 37th percentile) |
| **Executive Risk** | High |

**Summary:** Insufficient granularity of access control in Active Directory Federation Services allows an authorized attacker to elevate privileges locally.

➡️ [Executive Report](Investigation/CVE/CVE-2026-56155/CVE-2026-56155_CEO_REPORT.md)

</details>

<details>
<summary><b>CVE-2026-60137</b> — 🟡 WordPress SQL Injection <img src="https://img.shields.io/badge/MEDIUM-FFD700?style=flat-square"/> <img src="https://img.shields.io/badge/Risk-HIGH-FF8C00?style=flat-square"/></summary>
<br>

| Metric | Value |
|--------|-------|
| **CVSS Vector** | `AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:N/A:N` |
| **Weaknesses** | CWE-89 (SQL Injection) |
| **EPSS** | 4.03% (∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎ 79th percentile) |
| **GitHub PoCs** | 10 exploits — `Icex0/wp2shell-poc` (★ 437 stars) |
| **Executive Risk** | High (elevated due to public PoC availability) |

**Summary:** WordPress 6.8.x–7.0.x fails to sanitize `author__not_in` in `WP_Query`, enabling SQL injection. High-quality public PoCs drive risk to High.

➡️ [Executive Report](Investigation/CVE/CVE-2026-60137/CVE-2026-60137_CEO_REPORT.md)

</details>

<details>
<summary><b>CVE-2026-45138</b> — 🟡 CI4MS Stored XSS <img src="https://img.shields.io/badge/MEDIUM-FFD700?style=flat-square"/> <img src="https://img.shields.io/badge/Risk-MEDIUM-FFD700?style=flat-square"/></summary>
<br>

| Metric | Value |
|--------|-------|
| **CVSS Vector** | `AV:N/AC:L/PR:L/UI:R/S:C/C:L/I:L/A:N` |
| **Weaknesses** | CWE-79 (Cross-site Scripting) |
| **EPSS** | 0.15% (∎∎ 4th percentile) |
| **SSVC** | Automatable: `No` / Exploitation: `PoC` / Tech. Impact: `Partial` |

**Summary:** The `html_purify` validation uses by-reference mutation but CodeIgniter 4 passes a local copy — sanitized text is discarded and raw content stored unescaped, yielding stored XSS in any browser.

➡️ [Executive Report](Investigation/CVE/CVE-2026-45138/CVE-2026-45138_REPORT.md)

</details>

<details>
<summary><b>CVE-2026-56164</b> — 🟡 Microsoft SharePoint Server EoP <img src="https://img.shields.io/badge/MEDIUM-FFD700?style=flat-square"/> <img src="https://img.shields.io/badge/Risk-MEDIUM-FFD700?style=flat-square"/></summary>
<br>

| Metric | Value |
|--------|-------|
| **CVSS Vector** | `AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:L/A:L` |
| **Weaknesses** | CWE-306 (Missing Authentication for Critical Function) |
| **EPSS** | 5.60% (∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎∎ 84th percentile) |

**Summary:** Missing authentication for critical function in Microsoft Office SharePoint allows an unauthorized attacker to elevate privileges over a network.

➡️ [Executive Report](Investigation/CVE/CVE-2026-56164/CVE-2026-56164_CEO_REPORT.md)

</details>

<details>
<summary><b>🌐 Domain Intelligence</b> — 🔴 C2 Infrastructure <img src="https://img.shields.io/badge/CRITICAL-FF0000?style=flat-square"/> <img src="https://img.shields.io/badge/Risk-CRITICAL-FF0000?style=flat-square"/></summary>
<br>

| Metric | Value |
|--------|-------|
| **Indicator** | `morning-cell-6811.nukisora1808.workers.dev` |
| **Type** | Cloudflare Workers Subdomain |
| **Open Ports** | `80` `443` `2052` `2053` `2082` `2083` `2086` `2087` `2095` `2096` `8080` `8443` `8880` |
| **Suspected Actor** | TA505 (financially motivated — BEC, malware distribution) |
| **MITRE Techniques** | T1190 (Exploit Public-Facing App) · T1573 (Encrypted Channel) |

**Summary:** Cloudflare Workers subdomain exhibiting extensive open port exposure and encrypted channel patterns consistent with C2 infrastructure. High abuse confidence across all intelligence sources.

➡️ [Executive Report](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/morning-cell-6811.nukisora1808.workers.dev_CEO_REPORT.md)

</details>

---

## 🏗️ Repository Structure

```
Threat_Intelligence_portfolio/
├── README.md
└── Investigation/
    ├── CVE/
    │   ├── CVE-2026-44359/          # 🔴 Meshtastic — CI Poisoning (CVSS 10.0)
    │   ├── CVE-2026-45659/          # 🔴 Microsoft SharePoint — RCE (CVSS 8.8)
    │   ├── CVE-2026-56155/          # 🔴 Microsoft AD FS — EoP (CVSS 7.8)
    │   ├── CVE-2026-60137/          # 🟡 WordPress — SQLi (CVSS 5.9)
    │   ├── CVE-2026-45138/          # 🟡 CI4MS — Stored XSS (CVSS 5.4)
    │   └── CVE-2026-56164/          # 🟡 Microsoft SharePoint — EoP (CVSS 5.3)
    └── domain/
        └── morning-cell-6811.nukisora1808.workers.dev/   # 🔴 C2 Infrastructure
```

Each investigation directory contains:

| Module | Description |
|--------|-------------|
| 📁 `CVE_INVESTIGATION/` | Technical CVE enrichment — CVSS, EPSS, CWE, references |
| 📁 `THREAT_INTEL_INVESTIGATION/` | Threat actor context, CISA KEV cross-reference |
| 📁 `MITRE_INVESTIGATION/` | ATT&CK technique mapping & mitigations |
| 📁 `MALWARE_INVESTIGATION/` | Malware telemetry — MalwareBazaar, ThreatFox, URLhaus |
| 📁 `IOC_INVESTIGATION/` | Indicators of Compromise — Shodan, Censys, OTX |
| 📁 `EXPLOIT_INVESTIGATION/` | Exploit reconnaissance — Exploit-DB, GitHub |
| 📁 `FULL_REPORT_TOOL/` | Aggregated multi-agent pipeline output |
| 📄 `*_CEO_REPORT.md` | Executive report — risk assessment & remediation |

---

## 🔬 Methodology

| # | Stage | Data Sources |
|:-:|-------|--------------|
| 1 | **CVE Enrichment** | NVD · CIRCL · Vulners · OpenCVE · GitHub Security Advisories |
| 2 | **Threat Context** | CISA KEV Catalog · Threat Actor / Ransomware Association |
| 3 | **MITRE ATT&CK** | MITRE ATT&CK v14 — Heuristic + Evidence-Based Mapping |
| 4 | **Malware Telemetry** | MalwareBazaar · ThreatFox · URLhaus · Pulsedive · VirusTotal |
| 5 | **IOC Collection** | AbuseIPDB · AlienVault OTX · Shodan · Censys |
| 6 | **Exploit Recon** | Exploit-DB · GitHub Public Repository Search |
| 7 | **Executive Reporting** | SSVC v2.0.3 Scoring · Risk Assessment · Remediation Directives |

---

## 📡 Intelligence Sources

| Category | Sources |
|----------|---------|
| **CVE Enrichment** | <img src="https://img.shields.io/badge/-NVD-0033A0?style=flat-square"/> <img src="https://img.shields.io/badge/-CIRCL-00BFFF?style=flat-square"/> <img src="https://img.shields.io/badge/-Vulners-00B368?style=flat-square"/> <img src="https://img.shields.io/badge/-OpenCVE-1E90FF?style=flat-square"/> <img src="https://img.shields.io/badge/-OSV-FF6F00?style=flat-square"/> <img src="https://img.shields.io/badge/-Snyk-4C4CFF?style=flat-square"/> |
| **Threat Intelligence** | <img src="https://img.shields.io/badge/-CISA_KEV-FF0000?style=flat-square"/> <img src="https://img.shields.io/badge/-GitHub_Advisories-181717?style=flat-square"/> <img src="https://img.shields.io/badge/-AttackerKB-FF4500?style=flat-square"/> |
| **Malware Telemetry** | <img src="https://img.shields.io/badge/-MalwareBazaar-FF4444?style=flat-square"/> <img src="https://img.shields.io/badge/-ThreatFox-8B0000?style=flat-square"/> <img src="https://img.shields.io/badge/-URLhaus-CC0000?style=flat-square"/> <img src="https://img.shields.io/badge/-Pulsedive-4B0082?style=flat-square"/> |
| **Infrastructure Intel** | <img src="https://img.shields.io/badge/-Shodan-FF4444?style=flat-square"/> <img src="https://img.shields.io/badge/-Censys-008080?style=flat-square"/> <img src="https://img.shields.io/badge/-AlienVault_OTX-00BFFF?style=flat-square"/> |
| **Exploit Intel** | <img src="https://img.shields.io/badge/-Exploit_DB-FF6600?style=flat-square"/> <img src="https://img.shields.io/badge/-GitHub_Search-181717?style=flat-square"/> |
| **Frameworks** | MITRE ATT&CK v14 · SSVC v2.0.3 · CVSS 3.1 · CWE |

---

<p align="center">
  <i>Maintained for educational and professional demonstration purposes.</i>
  <br>
  <img src="https://img.shields.io/badge/Threat_Intelligence_Portfolio-v1.0-00ADD8?style=for-the-badge"/>
  <img src="https://img.shields.io/github/last-commit/ChPratik/Threat_intelligence_Portfolio?style=for-the-badge&color=00B368"/>
</p>
