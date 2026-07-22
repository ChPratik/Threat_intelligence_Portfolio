<p align="center">
  <img src="https://img.shields.io/badge/MITRE_ATT&CK-v14-2c2c2c?style=flat-square"/>
  <img src="https://img.shields.io/badge/CVSS-3.1-2c2c2c?style=flat-square"/>
  <img src="https://img.shields.io/badge/EPSS-FIRST-2c2c2c?style=flat-square"/>
  <img src="https://img.shields.io/badge/Sigma-Enabled-2c2c2c?style=flat-square"/>
  <img src="https://img.shields.io/badge/MISP-Integrated-2c2c2c?style=flat-square"/>
</p>

<h1 align="center">⚡ Threat Intelligence Portfolio</h1>

<p align="center">
  Professional vulnerability investigations combining threat analysis, detection engineering,<br>
  ATT&CK mapping, IOC enrichment, and executive reporting.
</p>

<br>

---

## 📊 At a Glance

<p align="center">
  <b>7</b> Active Investigations · 
  <b>Medium – Critical</b> Risk Range · 
  <b>567</b> Sigma Rules (repo) · 
  <b>20+</b> Intel Sources
</p>

---

## 🔍 Investigations

| CVE ID | Product | Type | CVSS | EPSS | Detection | Status |
|--------|---------|------|:----:|:----:|:---------:|--------|
| [CVE-2026-44359](Investigation/CVE/CVE-2026-44359/FULL_REPORT_TOOL/CVE-2026-44359_CEO_REPORT.md) | Meshtastic Firmware | CI Poisoning — Arbitrary Code Execution | **10.0** 🔴 `██████████` | 1.00% `██░░░░░░░░` | Σ 567 · YARA 0 | ✅ Patched |
| [CVE-2026-45659](Investigation/CVE/CVE-2026-45659/FULL_REPORT_TOOL/CVE-2026-45659_CEO_REPORT.md) | Microsoft SharePoint | Deserialization — Remote Code Execution | **8.8** 🟠 `████████░░` | 3.22% `████░░░░░░` | Σ 74 · YARA 0 | 🔴 Open |
| [CVE-2026-56155](Investigation/CVE/CVE-2026-56155/FULL_REPORT_TOOL/CVE-2026-56155_CEO_REPORT.md) | Microsoft AD FS | Elevation of Privilege | **7.8** 🟠 `███████░░░` | 0.38% `░░░░░░░░░░` | Σ 1 · YARA 0 | 🔴 Open |
| [CVE-2026-60137](Investigation/CVE/CVE-2026-60137/FULL_REPORT_TOOL/CVE-2026-60137_CEO_REPORT.md) | WordPress < 7.0.2 | SQL Injection — WP_Query | **5.9** 🟡 `█████░░░░░` | 4.03% `█████░░░░░` | Σ 528 · YARA 0 | ✅ Patched |
| [CVE-2026-45138](Investigation/CVE/CVE-2026-45138/FULL_REPORT_TOOL/CVE-2026-45138_CEO_REPORT.md) | CI4MS CMS ERP | Stored XSS — Validation Bypass | **5.4** 🟡 `█████░░░░░` | 0.15% `░░░░░░░░░░` | Σ 30 · YARA 0 | ✅ Patched |
| [CVE-2026-56164](Investigation/CVE/CVE-2026-56164/FULL_REPORT_TOOL/CVE-2026-56164_CEO_REPORT.md) | Microsoft SharePoint Server | Elevation of Privilege | **5.3** 🟡 `█████░░░░░` | 5.60% `██████░░░░` | Σ 528 · YARA 0 | 🔴 Open |

### 🌐 Infrastructure Intelligence

| Indicator | Type | Suspected Actor | Risk | Status |
|-----------|------|-----------------|:----:|--------|
| `morning-cell-6811.nukisora1808.workers.dev` | C2 — Cloudflare Workers | TA505 *(low confidence)* | 🔴 Critical | 🟢 Active |

---

## 🧩 Capabilities

| 🛡️ Vulnerability Analysis | 🌍 Threat Intelligence | ⚙️ Detection Engineering |
|---------------------------|------------------------|--------------------------|
| CVSS scoring · EPSS probability | CISA KEV cross-reference | Sigma correlation rules |
| CWE classification | Threat actor association | YARA signature generation |
| Affected version mapping | Campaign link analysis | Suricata / Snort rules |
| Vendor advisory references | Exploitation status tracking | Splunk · Wazuh · Defender · Elastic |

| 📍 IOC Intelligence | 🗺️ ATT&CK Analysis | 📋 Executive Reporting |
|---------------------|---------------------|------------------------|
| Domains · URLs · IPv4/IPv6 | MITRE ATT&CK v14 mapping | Business impact summary |
| File hashes (MD5/SHA1/SHA256) | Tactic & technique classification | Risk assessment & prioritization |
| Email indicators | Mitigation identification | Confidence statements |
| Multi-source aggregation | Heuristic inference | Remediation directives |

---

## 🔄 Investigation Workflow

<p align="center">
  <b>🔍 CVE</b> → <b>⚙️ Technical Analysis</b> → <b>🌐 Threat Context</b> → <b>🗺️ ATT&CK</b> → <b>🛡️ Detection</b> → <b>📍 IOC Collection</b> → <b>📋 Report</b>
</p>

Each investigation produces an **11-section intelligence report**:

| # | Section | Description |
|---|---------|-------------|
| 1 | 📌 Executive Summary | Concise briefing for decision-makers |
| 2 | 📖 Facts | Verified intelligence with source attribution and confidence |
| 3 | 🔎 Analysis | Contextual interpretation of raw data |
| 4 | ⚠️ Risk Assessment | Business impact, priority, confidence |
| 5 | 🔬 Technical Analysis | Root cause, attack path, exploitation |
| 6 | 🗺️ MITRE ATT&CK Map | Techniques, tactics, mitigations |
| 7 | 🛡️ Detection Rules | Sigma, YARA, Suricata, Splunk, Wazuh, Defender, Elastic |
| 8 | 📍 IOC Table | Machine-readable indicators with confidence scores |
| 9 | 🧬 MISP Context | Galaxy clusters, taxonomy tags, sightings |
| 10 | 📊 Evidence Matrix | Source attribution for all intelligence |
| 11 | 🎯 Directed Mandate | Prioritized remediation with deadlines |

---

## 📡 Intelligence Coverage

| Domain | Coverage |
|--------|----------|
| 🔬 **Technical Intel** | CVE · CVSS · CWE · EPSS · Vendor Advisories |
| 🕵️ **Threat Intel** | Threat Actors · Campaigns · CISA KEV · Exploitation Status |
| 🏗️ **Infrastructure** | Domains · Hosting · ASN · Certificates · Reputation |
| 🛡️ **Detection** | Sigma · YARA · Snort · Suricata · Splunk · Wazuh · Defender · Elastic |
| 📍 **IOC** | Domains · URLs · IPs · Hashes · Email |

---

## 🛠️ Technology Stack

| Category | Technologies |
|----------|--------------|
| 🐍 Analysis | Python · SQLite · ChromaDB |
| 🧠 Threat Intelligence | MITRE ATT&CK v14 · CISA KEV · MISP · SSVC v2.0.3 |
| 🔬 Vulnerability Intel | NVD · CIRCL · Vulners · OpenCVE · OSV · GitHub Security Advisories |
| ⚙️ Detection Engineering | Sigma · YARA · Suricata |
| 🦠 Malware Telemetry | MalwareBazaar · ThreatFox · URLhaus · Pulsedive · VirusTotal |
| 🌍 Infrastructure Intel | Shodan · Censys · AlienVault OTX · AbuseIPDB |
| 💥 Exploit Intelligence | Exploit-DB · GitHub Security Lab |

---

<p align="center">
  <b>🎯 Designed for</b><br>
  Threat Intelligence · Detection Engineering · Incident Response · Vulnerability Management · Security Research
  <br><br>
  <img src="https://img.shields.io/github/last-commit/ChPratik/Threat_intelligence_Portfolio?style=flat-square&color=555"/>
  <br><br>
  <i>Maintained for professional demonstration purposes.</i>
</p>
