# Amazon 2023 CIS Audit - 26th June 2023

## CIS Benchmark 2.0.0
## 2.0.0 based on v2.0.0

- full rewrite for CIS Amazon Linux 2023 Benchmark v2.0.0, built from the RHEL9-CIS-Audit v3.0.0 content
- 342 controls in 7 sections
- goss.yml renamed syver.yml, syverfile includes
- run_audit.sh uses syver v0.16.0 by default, BENCHMARK_VER 2.0.0
- README describes syver
- discovery for partitions, cron, at, backup files, faillock and network directories
- opt-outs skipped with a reason instead of omitted
- meta server levels match the benchmark, workstation NA
- 1.1.1.x kernel modules checked with modprobe --showconfig and /sys/module
- 1.1.1.5 unused filesystem kernel modules check added
- 1.1.2.1.2 to 1.1.2.1.4 tmp.mount Options read correctly
- 1.2.1.1 checks the Amazon Linux key
- 1.2.2.1 checks for a newer Amazon Linux release
- 1.4.2 grub and /boot/efi file modes and fstab options checked
- 1.7.1 benchmark motd script
- 2.1.x package and service names for AL2023, masked services checked with service masked
- 2.1.17 checks ports 25, 465, 587 and postconf inet_interfaces
- 2.3.2 reads chrony sourcedir and confdir sources
- 2.4.x checks skipped when cronie or at is not installed
- 3.1.1 kernel method checks ipv6.disable on every boot entry
- 3.3.2.1 force_forwarding check added
- 4.1.4 and 4.1.11 fail when no zone is active
- 5.3.2.5 authselect check skipped when the role does not manage authselect
- 5.3.3.3.x pam_pwhistory arguments checked in system-auth and password-auth
- 6.1.2.x rsyslog checks depend on package:rsyslog
- 6.2.3.x audit rules accept the -a always,exit -F path/dir form
- 6.2.3.9 /etc/systemd/network and 6.2.3.34 audit task list checks added
- 6.2.3.23 faillock rule skipped when /var/run/faillock does not exist
- 7.1.1 to 7.1.10 typed file tests, mode or more restrictive

## 1.3.1 based on v1.0.0

- 5.1.3: lastlog typo fixed, lastlog/wtmp/btmp checked against benchmark modes
- 4.6.1.4: flags only accounts with no, negative or over-30 inactive value; INACTIVE default range fixed
- 4.6.5: checks login.defs and every shell initialization file for weak umask
- 2.2.17: masked rpcbind.socket accepted (is-enabled exits 1)
- 6.2.2: checks empty password fields, not locked accounts
- 6.1.11: symlinks excluded, sticky-bit directories allowed
- 6.2.10: no false fail without interactive users, pwck exit codes accepted
- 4.3.3: broken sudoers.d check removed
- 4.4.1: skipped unless custom profile create and select are enabled
- 1.6.1.x: goss files renamed to match their control IDs
- 1.7.x, 3.2.x, 5.1.1.1-2: split into one file per control
- 1.7.3: stray "& 6" removed from title
- 2.2.9: cyrus-imapd package name typo, package parent no longer gated on dovecot
- 5.1.1.2: own rule gate and CIS_ID
- 4.2.3: perms test variable typo and 0133 mask
- 4.6.2: benchmark audit commands, exec no longer calls /awk
- 3.4.2.7: exit-status accepts 1 when grep -v returns nothing
- 3.1.1: grub ipv6.disable tests removed, sysctl method only
- 5.2.3.5, 5.2.3.9, 5.2.3.13, 5.2.3.19: rule file patterns accept -k and filtered syscall lists
- 5.2.3.13: b64 rule checked
- 1.6.1.4: getenforce output pattern
- 2.1.2: grep -h so server anchors match
- 4.2.4: directive patterns without colon, gated per variable
- 5.1.1.6: gated on remote_log_server, omfwd target matched
- 2.2.1, 2.2.4, 2.3.3: package names xorg-x11-server-common, dhcp-server, ftp
- 1.1.7.1, 1.2.4, 2.2.1: level_2 gates
- 6.1.10: rpm -Va output piped instead of redirected
- run_audit.sh: os-release fallback for report metadata
- LICENSE: MindPoint Group - A Quantum Sky Company
- 1.1.7.2, 1.1.7.3, 1.6.1.5: blank line after document start
- 1.3.3, 1.4.1, 1.9, 2.1.1-2, 4.2.14, 4.3.5-6, 4.6.1.5, 4.6.6, 5.1.1.1-7, 5.1.2.x, 5.1.3: level_1 gates
- 1.1.3.2-3, 1.1.7.2-3, 1.6.1.5, 4.2.13: meta server level matches benchmark profile
- 1.3.3, 4.2.4, 4.2.14, 4.3.5, 4.4.1-2, 4.6.6, 5.1.2.x, 5.1.3, 5.2.1.4: meta workstation NA
- 1.2.2, 1.2.4: repo file checks work across multiple .repo files
- 1.2.2, 1.2.4: dnf.conf must set the key to 1
- 4.2.14: any CRYPTO_POLICY line fails
- 4.2.19: effective sshd -T value, 1-60 seconds
- 4.3.2: broken sudoers.d check replaced with !use_pty check
- 4.3.2: use_pty accepted in /etc/sudoers or /etc/sudoers.d
- 5.2.4.5-7: benchmark find commands, any non-compliant file fails
- 6.2.1: non-shadowed password fields detected
- 6.2.8: benchmark root PATH checks
- 6.2.9: UID 0 accounts other than root fail
- 6.2.11: .forward, .rhost(s) and loose .netrc files found
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
  - goss links updated
  - 1.4.1 and 3.3.3: removed blank line before the --- document start
  - .gitignore: secrets, QA artefact and .ansible patterns added

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
