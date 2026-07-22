# Plan: Fix README Data & Replace Block Bars with Shields.io Badges

## Changes to Make

### Part A — Fix data mismatches (verified from CEO reports)

| CVE | Field | Wrong Value | Correct Value |
|-----|-------|-------------|---------------|
| CVE-2026-45659 | CVSS | `8.8` 🟠 `████████░░` | `N/A` (report says "Not applicable") |
| CVE-2026-56155 | EPSS | `0.38%` `░░░░░░░░░░` | `3.79%` (report says 0.00379 / 3.79%) |
| CVE-2026-60137 | CVSS | `5.9` 🟡 `█████░░░░░` | `N/A` (report says "Not applicable") |
| CVE-2026-45138 | CVSS | `5.4` 🟡 `█████░░░░░` | `N/A` (report has no CVSS field) |
| CVE-2026-56164 | CVSS | `5.3` 🟡 `█████░░░░░` | `N/A` (report says "Not applicable") |

### Part B — Replace block bars with shields.io badges

Remove all `█████░░░░░` strings. Replace with `<img>` shields.io badges.

**CVSS badges** (color-coded by severity):
- `10.0` → `https://img.shields.io/badge/CVSS-10.0-cc0000?style=flat-square`
- `7.8` → `https://img.shields.io/badge/CVSS-7.8-e05d44?style=flat-square`
- `N/A` → `https://img.shields.io/badge/CVSS-N%2FA-555?style=flat-square`

**EPSS badges** (color-coded by likelihood):
- `1.00%` → `https://img.shields.io/badge/EPSS-1.00%25-dfb317?style=flat-square` (yellow)
- `3.22%` → `https://img.shields.io/badge/EPSS-3.22%25-e05d44?style=flat-square` (orange)
- `3.79%` → `https://img.shields.io/badge/EPSS-3.79%25-e05d44?style=flat-square` (orange)
- `4.03%` → `https://img.shields.io/badge/EPSS-4.03%25-e05d44?style=flat-square` (orange)
- `0.15%` → `https://img.shields.io/badge/EPSS-0.15%25-007ec6?style=flat-square` (blue)
- `5.60%` → `https://img.shields.io/badge/EPSS-5.60%25-e05d44?style=flat-square` (orange)

### Resulting Table

```
| CVE ID | Product | Type | CVSS | EPSS | Σ HC/Rel | Status |
|--------|---------|------|:----:|:----:|:--------:|--------|
| CVE-2026-44359 | Meshtastic Firmware | CI Poisoning — Arbitrary Code Execution | <img src="...CVSS-10.0-cc0000..."/> | <img src="...EPSS-1.00%25-dfb317..."/> | 0/567 | ✅ Patched |
| CVE-2026-45659 | Microsoft SharePoint | Deserialization — Remote Code Execution | <img src="...CVSS-N%2FA-555..."/> | <img src="...EPSS-3.22%25-e05d44..."/> | 7/67 | 🔴 Open |
| CVE-2026-56155 | Microsoft AD FS | Elevation of Privilege | <img src="...CVSS-7.8-e05d44..."/> | <img src="...EPSS-3.79%25-e05d44..."/> | 0/1* | 🔴 Open |
| CVE-2026-60137 | WordPress < 7.0.2 | SQL Injection — WP_Query | <img src="...CVSS-N%2FA-555..."/> | <img src="...EPSS-4.03%25-e05d44..."/> | 0/528 | ✅ Patched |
| CVE-2026-45138 | CI4MS CMS ERP | Stored XSS — Validation Bypass | <img src="...CVSS-N%2FA-555..."/> | <img src="...EPSS-0.15%25-007ec6..."/> | 0/30 | ✅ Patched |
| CVE-2026-56164 | Microsoft SharePoint Server | Elevation of Privilege | <img src="...CVSS-N%2FA-555..."/> | <img src="...EPSS-5.60%25-e05d44..."/> | 99/429 | 🔴 Open |
```
