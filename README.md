<p align="center">
  <img src="https://img.shields.io/badge/MITRE_ATT&CK-v14-EE2C2C?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/CVSS-3.1-005BAA?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/EPSS-FIRST-00B368?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Sigma-Ready-FD0?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/YARA-Ready-FF4444?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/MISP-Enabled-8B0000?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/SSVC-v2.0.3-4B0082?style=for-the-badge"/>
</p>

<h1 align="center">Threat Intelligence Portfolio</h1>

<p align="center">
  Professional vulnerability investigations combining<br>
  <b>threat analysis · detection engineering · ATT&CK mapping · IOC enrichment · executive reporting</b>
</p>

<br>

---

## Investigations

| CVE ID | Product | Type | Severity | Detection | Status |
|--------|---------|------|:---------:|:---------:|--------|
| [CVE-2026-44359](Investigation/CVE/CVE-2026-44359/FULL_REPORT_TOOL/CVE-2026-44359_CEO_REPORT.md) | Meshtastic Firmware | CI Poisoning — Arbitrary Code Execution | <img src="https://img.shields.io/badge/10.0-CRITICAL-FF0000?style=flat-square"/> | <img src="https://img.shields.io/badge/Σ-567-FFD700?style=flat-square"/> <img src="https://img.shields.io/badge/YARA-0-FF4444?style=flat-square"/> | ✅ Patched |
| [CVE-2026-45659](Investigation/CVE/CVE-2026-45659/FULL_REPORT_TOOL/CVE-2026-45659_CEO_REPORT.md) | Microsoft SharePoint | Deserialization — Remote Code Execution | <img src="https://img.shields.io/badge/8.8-HIGH-FF8C00?style=flat-square"/> | <img src="https://img.shields.io/badge/Σ-567-FFD700?style=flat-square"/> <img src="https://img.shields.io/badge/YARA-0-FF4444?style=flat-square"/> | 🔴 Open |
| [CVE-2026-56155](Investigation/CVE/CVE-2026-56155/FULL_REPORT_TOOL/CVE-2026-56155_CEO_REPORT.md) | Microsoft AD FS | Elevation of Privilege | <img src="https://img.shields.io/badge/7.8-HIGH-FF8C00?style=flat-square"/> | <img src="https://img.shields.io/badge/Σ-567-FFD700?style=flat-square"/> <img src="https://img.shields.io/badge/YARA-0-FF4444?style=flat-square"/> | 🔴 Open |
| [CVE-2026-60137](Investigation/CVE/CVE-2026-60137/FULL_REPORT_TOOL/CVE-2026-60137_CEO_REPORT.md) | WordPress < 7.0.2 | SQL Injection — WP_Query | <img src="https://img.shields.io/badge/5.9-MEDIUM-FFD700?style=flat-square"/> | <img src="https://img.shields.io/badge/Σ-567-FFD700?style=flat-square"/> <img src="https://img.shields.io/badge/YARA-0-FF4444?style=flat-square"/> | ✅ Patched |
| [CVE-2026-45138](Investigation/CVE/CVE-2026-45138/FULL_REPORT_TOOL/CVE-2026-45138_CEO_REPORT.md) | CI4MS CMS ERP | Stored XSS — Validation Bypass | <img src="https://img.shields.io/badge/5.4-MEDIUM-FFD700?style=flat-square"/> | <img src="https://img.shields.io/badge/Σ-567-FFD700?style=flat-square"/> <img src="https://img.shields.io/badge/YARA-0-FF4444?style=flat-square"/> | ✅ Patched |
| [CVE-2026-56164](Investigation/CVE/CVE-2026-56164/FULL_REPORT_TOOL/CVE-2026-56164_CEO_REPORT.md) | Microsoft SharePoint Server | Elevation of Privilege | <img src="https://img.shields.io/badge/5.3-MEDIUM-FFD700?style=flat-square"/> | <img src="https://img.shields.io/badge/Σ-567-FFD700?style=flat-square"/> <img src="https://img.shields.io/badge/YARA-0-FF4444?style=flat-square"/> | 🔴 Open |

## Infrastructure Intelligence

| Indicator | Type | Suspected Actor | Risk | Status |
|-----------|------|-----------------|:----:|--------|
| [`morning-cell-6811.nukisora1808.workers.dev`](Investigation/domain/morning-cell-6811.nukisora1808.workers.dev/morning-cell-6811.nukisora1808.workers.dev_CEO_REPORT.md) | C2 — Cloudflare Workers | TA505 *(low confidence)* | <img src="https://img.shields.io/badge/CRITICAL-FF0000?style=flat-square"/> | 🟢 Active |

---

## What Every Investigation Includes

### Vulnerability Analysis
CVSS scoring · EPSS probability · CWE classification · Affected versions · Vendor advisory references

### Threat Intelligence
Threat actor correlation · CISA KEV cross-reference · Campaign association · Exploitation status

### Detection Engineering
Sigma rules · YARA signatures · Suricata/Snort rules · Splunk queries · Wazuh · Microsoft Defender · Elastic

### IOC Intelligence
Domains · URLs · IPv4/IPv6 · File hashes (MD5/SHA1/SHA256) · Email indicators

### ATT&CK Analysis
MITRE ATT&CK v14 techniques · Tactic mapping · Mitigation identification · Heuristic inference

### Executive Reporting
Business impact summary · Risk assessment · Confidence statements · Remediation directives

---

## Investigation Workflow

```
CVE Publication
      ↓
Technical Analysis — Root cause, attack vector, exploitation complexity
      ↓
Threat Context — KEV status, threat actor correlation, campaign association
      ↓
MITRE ATT&CK Mapping — Technique identification, tactic classification, mitigation recommendations
      ↓
Detection Engineering — Sigma correlation, YARA generation, SIEM query development
      ↓
IOC Collection — Multi-source aggregation, enrichment, confidence scoring, MISP taxonomization
      ↓
Executive Assessment — Risk prioritization, business impact, remediation mandate, confidence rating
```

---

## Report Structure

Every investigation follows this intelligence cycle:

| Section | Description |
|---------|-------------|
| **Executive Summary** | Concise briefing for decision-makers |
| **Facts** | Verified intelligence with source attribution and confidence |
| **Analysis** | Contextual interpretation of raw data |
| **Risk Assessment** | Business impact, priority, and confidence |
| **Technical Analysis** | Root cause, attack path, exploitation details |
| **MITRE ATT&CK Map** | Techniques, tactics, mitigations with inference confidence |
| **Detection Rules** | Sigma, YARA, Suricata, Splunk, Wazuh, Defender, Elastic |
| **IOC Table** | Machine-readable indicators with confidence scores |
| **MISP Context** | Galaxy clusters, taxonomy tags, sightings |
| **Evidence Matrix** | Source attribution for all intelligence |
| **Directed Mandate** | Prioritized remediation actions with deadlines |

---

## Intelligence Coverage

```
Technical Intelligence
  CVE · CVSS · CWE · EPSS · Vendor Advisories

Threat Intelligence
  Threat Actors · Campaigns · CISA KEV · Exploitation Status

Infrastructure
  Domains · Hosting · ASN · Certificates · Reputation

Detection
  Sigma · YARA · Snort · Suricata · Splunk · Wazuh · Defender · Elastic

IOC
  Domains · URLs · IPs · Hashes · Email
```

---

## Technology Stack

| Category | Technologies |
|----------|--------------|
| **Analysis** | Python · SQLite · ChromaDB |
| **Threat Intelligence** | MITRE ATT&CK v14 · CISA KEV · MISP · SSVC v2.0.3 |
| **Vulnerability Intel** | NVD · CIRCL · Vulners · OpenCVE · OSV · GitHub Security Advisories |
| **Detection** | Sigma · YARA · Suricata |
| **Malware Telemetry** | MalwareBazaar · ThreatFox · URLhaus · Pulsedive · VirusTotal |
| **Infrastructure Intel** | Shodan · Censys · AlienVault OTX · AbuseIPDB |
| **Exploit Intel** | Exploit-DB · GitHub Security Lab |

---

<p align="center">
  <b>Designed for</b><br>
  Threat Intelligence · Detection Engineering · Incident Response · Vulnerability Management · Security Research
  <br><br>
  <img src="https://img.shields.io/badge/Threat_Intelligence_Portfolio-v1.0-00ADD8?style=for-the-badge"/>
  <img src="https://img.shields.io/github/last-commit/ChPratik/Threat_intelligence_Portfolio?style=for-the-badge&color=00B368"/>
  <br><br>
  <i>Maintained for professional demonstration purposes.</i>
</p>
