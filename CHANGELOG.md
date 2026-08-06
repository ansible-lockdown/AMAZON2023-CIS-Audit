# Amazon 2023 CIS Audit - 26th June 2023

## 1.3.1 based on v1.0.0

- Aug26_align branch
  - 4.4.2: pam_failock -> pam_faillock, repointed to /etc/pam.d files
  - 1.1.7.3: nonosuid -> nosuid
  - 4.5.4: stray space in md5 negation regex
  - 4.3.4: sudoers.d check had 4.3.3 rule ID and title
  - 15 titles realigned to v1.0.0 benchmark, including 6.1.3-6.1.9 and 6.1.11-6.1.12 off-by-one
  - 1.1.9 and 3.1.1 retitled from legacy short forms
  - 6.1.13: SUID and SGID sub-checks disambiguated
  - 4.5.2: faillock.conf deny and unlock_time checks added
  - 4.5.4: libuser.conf and login.defs checks added
  - 4.2.14: /etc/sysconfig/sshd added to exec
  - 1.2.4: yum.conf -> dnf.conf
  - .yamllint: invalid indent-spaces key replaced, repo now lints
  - vars/CIS.yml: comment spacing

## 2026_MAY_QA2

- 2026 May follow-up QA pass
  - Fixed amzn2023cis_warning_banner typo in vars/CIS.yml: "Authorized uses" -> "Authorized users"
  - Aligned with remediation repo 2026_MAY_QA2

## 1.3.0 based on v1.0.0 - Branch 2026_MAY_QA

- 2026_MAY_QA branch
  - Added missing toggle: amzn2023cis_rule_6_1_13 to vars/CIS.yml
  - Fixed run_audit.sh container OS detection: added /etc/os-release fallback for Amazon Linux
  - Fixed LICENSE company name casing: MindPoint Group (capital P)
  - Aligned with remediation repo v1.3.0 QA pass
  - Fixed cis_4.2.20: ClientAliveInterval/CountMax variable references were swapped
  - Reverted cis_1.7.x permission check paths back to /etc/issue and /etc/issue.net per CIS benchmark (remediation now removes symlinks and writes regular files)
  - Fixed 6.1.x off-by-one: renumbered audit tests cis_6.1.2-12 to cis_6.1.3-13, added new cis_6.1.2 for CIS duplicate /etc/passwd entry (addresses #162)
