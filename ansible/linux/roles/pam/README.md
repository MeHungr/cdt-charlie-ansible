# pam role
Enforces password complexity and aging policy via PAM, and manages a set of accounts includes create required ones and lock stale/unauthorized ones.

# Requirements
- Debian/Ubuntu target (need becuase of apt, package libpam-pwquality, and PAM config expected at
  /etc/pam.d/common-password). 

# Before running
Edit vars/main.yml:
- pam_min_length / pam_min_complexity_classes - password policy strictness
- pam_max_days / pam_warn_days - password aging
- pam_accounts_present / pam_accounts_locked - account lists.

# Usage
ansible-playbook -i inventory site.yml --limit linux_targets --tags pam


# Features demonstrated
1. Package install + PAM stack config
2. Password complexity policy via config templating
3. Password aging policy
4. Account lifecycle management - create/lock accounts