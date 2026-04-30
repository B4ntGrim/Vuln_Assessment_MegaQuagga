# Vuln_Assessment_MegaQuagga
Nessus-based vulnerability assessment of the MegaQuagga environment identifying 47 vulnerabilities across three hosts — 27 Critical, 14 High. Includes executive summary, full CVSS-scored remediation list, and priority-ranked findings targeting outdated PHP, Ubuntu system packages, and SSL/TLS weaknesses.
# Vulnerability Assessment — MegaQuagga Environment

**Analyst:** Samuel Weiss
**Organization:** 0x2A Security
**Assessment Dates:** April 14–15, 2026
**Environment:** MegaQuagga.local

---

## Overview

This project documents a **Nessus-based vulnerability assessment** conducted across three hosts in the MegaQuagga environment. The assessment identified 47 total vulnerabilities, prioritized by CVSS score and exploitability impact, and produced a structured remediation list mapped to each affected asset.

---

## Files

| File | Description |
|------|-------------|
| `_VULN_ASSESSMENT__MegaQuagga_VA_-_Executive_Summary__Samuel_Weiss_.docx` | Executive summary of findings, critical vulnerability breakdown by host, remediation patterns, and recommended next steps |
| `_VULN_ASSESSMENT__MegaQuagga_VA_-_Remediation_List__Samuel_Weiss_.xlsx` | Full vulnerability worksheet including asset, severity, CVSS score, Nessus plugin ID, CVE, solution, exploitability, impact, and calculated priority ranking |

---

## Scope

- **Hosts Scanned:** 3 targets within the MegaQuagga.local network (10.20.30.10, 10.20.30.11, 10.20.30.12)
- **Tool Used:** Nessus Vulnerability Scanner
- **Total Vulnerabilities Found:** 47

---

## Vulnerability Summary

| Severity | Count |
|----------|-------|
| Critical | 27 |
| High | 14 |
| Medium | 5 |
| Low | 1 |
| Informational | 0 |
| **Total** | **47** |

---

## Critical Findings by Host

### 10.20.30.10 (megaquagga.local) — 4 Critical
All critical findings stem from an **outdated and unsupported PHP version**:
- PHP Unsupported Version Detected (CVSS 10.0 — Priority 10, highest in assessment)
- PHP 8.2.x vulnerabilities across multiple versions (CVSS 9.8 each)
- Remediation: Upgrade PHP to the latest supported release (8.2.30+)

### 10.20.30.12 — 23 Critical
The most severely exposed host in the assessment. All 23 critical vulnerabilities are caused by **outdated Ubuntu system packages**, including:
- Redis, OpenSSL, Kerberos, Python, SQLite, Ruby, BusyBox, libxml2, GLib, Perl, and more
- CVSS scores ranging from 9.0 to 9.9
- Remediation: Run `apt upgrade` or equivalent — a single maintenance window resolves virtually all findings

### 10.20.30.11 — 0 Critical
No critical vulnerabilities. Presents SSL/TLS weaknesses:
- SWEET32 attack (weak cipher suites) — High severity (CVSS 7.5)
- Self-signed and untrusted SSL certificates — Medium severity (CVSS 6.5)
- SMB signing not required — Medium severity
- Remediation: Replace self-signed certificates and disable legacy cipher suites

---

## Remediation Priority Order

1. **Apply all system package updates on 10.20.30.12** — eliminates 23 of 27 critical vulnerabilities in a single maintenance window
2. **Upgrade PHP to a supported version on 10.20.30.10** — resolves all 4 remaining critical findings
3. **Address SSL/TLS configuration weaknesses on 10.20.30.11** — replaces self-signed certificates and disables vulnerable cipher suites

---

## Spreadsheet Structure (XLSX)

The remediation list workbook contains the following sheets:

- **VULNERABILITY ASSESSMENT** — Full vulnerability register with all 47 findings
- **Vulns by Asset** — Findings filtered and grouped per host
- **Top Vulnerabilities** — Priority-ranked view of all findings
- **Severity Distribution** — Count by severity level
- **Remediation List** — Prioritized action list with solution notes per finding

---

## GitHub Description

> Nessus-based vulnerability assessment of the MegaQuagga environment identifying 47 vulnerabilities across three hosts — 27 Critical, 14 High. Includes executive summary, full CVSS-scored remediation list, and priority-ranked findings targeting outdated PHP, Ubuntu system packages, and SSL/TLS weaknesses.
