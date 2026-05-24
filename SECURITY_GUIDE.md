# Security Best Practices for AI-CLAUDE-

This document outlines best practices to safeguard the repository and ensure that critical changes are monitored and controlled effectively.

---

### 1. **Branch Protection Rules**
Set branch protection rules for sensitive branches, including:
- Restrict direct pushes.
- Require approved pull requests for merging changes.
- Enable status checks for workflow validations.
- Prohibit branch deletion and force push actions.

#### Steps to Implement in GitHub:
1. Go to **Settings > Code and Automation > Branches.**
2. Add a branch rule for the sensitive branch (e.g., `no-watermark-support-gabriel-mahan`).
3. Select the restrictions based on your needs.

---

### 2. **Collaborator Access Management**

- Remove unnecessary collaborators or team members.
- Grant permissions sparingly (e.g., Read, Write, Admin).
- Enable **two-factor authentication** (2FA) for all collaborators.

---

### 3. **Activity Monitoring and Alerts**

- Use **GitHub Actions/Webhooks** to monitor repository activity.
- Alerts can notify you of branch creation, deletion, or abnormal activity.
- Review commit logs regularly.

#### Example GitHub Action for Monitoring:
```yaml
name: Monitor Repository Events
on:
  push:
    branches:
      - '*'
  delete:
    branches:
      - '*'

jobs:
  notify:
    runs-on: ubuntu-latest
    steps:
      - name: Notify Activity
        run: echo "Branch push or deletion detected."
```

---

### 4. **Codeowners for Sensitive Files**

Set up a `CODEOWNERS` file to ensure only authorized individuals can approve changes to sensitive files like `DIRECTIVES.md` or `.gitignore`.

#### Example `CODEOWNERS` File:
```
# CODEOWNERS File
# Require reviews by Gabriel Mahan for sensitive files
DIRECTIVES.md @gabemahan-code
.gitignore @gabemahan-code
```

---

### 5. **Private Repository Management**

If further privacy is required:
- Convert the repository to **Private** in **Settings > General > Repository Visibility**.
- Ensure only trusted collaborators have access.

---
