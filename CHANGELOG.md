# Amazon 2023 CIS Audit - 26th June 2023

## 1.3.0 based on v1.0.0

- 2026_MAY_QA branch
  - Added missing toggle: amzn2023cis_rule_6_1_13 to vars/CIS.yml
  - Fixed run_audit.sh container OS detection: added /etc/os-release fallback for Amazon Linux
  - Fixed LICENSE company name casing: MindPoint Group (capital P)
  - Aligned with remediation repo v1.3.0 QA pass
  - Fixed cis_4.2.20: ClientAliveInterval/CountMax variable references were swapped
  - Reverted cis_1.7.x permission check paths back to /etc/issue and /etc/issue.net per CIS benchmark (remediation now removes symlinks and writes regular files)
  - Fixed 6.1.x off-by-one: renumbered audit tests cis_6.1.2-12 to cis_6.1.3-13, added new cis_6.1.2 for CIS duplicate /etc/passwd entry (addresses #162)
