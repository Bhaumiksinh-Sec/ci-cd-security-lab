# ci-cd-security-lab
Learning CI/CD security and DevSecOps fundamentals from scratch.
Update: CI/CD security learning progress logged.

Goal: Build a DevSecOps-style CI/CD pipeline suite with security controls and least-privilege hardening.

## CI/CD Security Lab (GitHub Actions)

This repository is a personal learning lab to understand CI/CD security controls using GitHub Actions.
The focus is on building safe, observable automation (no cloud deployments yet).

### What’s included

#### 01 - First Safe CI/CD Workflow
- Purpose: Baseline workflow to confirm CI/CD runs successfully.
- Trigger: Runs on pushes to `main` and can also be run manually.
- Why it matters: Provides a reliable “pipeline health” signal.

#### 02 - Secret Scanning (Gitleaks)
- Purpose: Scan the repository for exposed secrets (tokens, keys, passwords).
- Trigger: Runs on pushes to `main`, but ignores workflow-only and README-only changes to reduce noise.
- Why it matters: Secret leaks are a common cause of GitHub and CI/CD compromise.

#### 03 - Dependency Vulnerability Scan (Trivy)
- Purpose: Scan repository contents for known HIGH/CRITICAL vulnerabilities.
- Trigger: Manual only (on-demand).
- Why it matters: Shows controlled security scanning without creating unnecessary pipeline noise.

### How to run workflows manually
1. Go to the **Actions** tab.
2. Select the workflow you want to run.
3. Click **Run workflow**.

### Notes
- Security scans are currently configured as non-blocking while learning.
- Future work will include stricter enforcement and (later) safe AWS integration using least-privilege IAM.



## Security Process

This repository follows a simple, security-first CI/CD process inspired by real-world SOC and DevSecOps practices.

### 1. Change Introduction
- Any change to the repository is treated as a potential security event.
- Direct commits to the `main` branch are restricted to enforce change control.

### 2. Automated Security Checks
- **Secret scanning (Gitleaks)** runs automatically on relevant changes to detect exposed credentials early.
- **Dependency vulnerability scanning (Trivy)** is run manually on demand to assess risk without creating unnecessary pipeline noise.

### 3. Review and Assessment
- CI/CD workflow results are reviewed through GitHub Actions logs.
- Findings are assessed based on severity, context, and exploitability rather than tool output alone.

### 4. Documentation
- Security findings and reviews are documented using a dedicated issue template.
- Each review records evidence, assessment, and outcome for audit and learning purposes.

### 5. Resolution and Closure
- If no action is required, findings are documented and closed.
- If remediation is needed, fixes are applied via pull request and revalidated through CI/CD.

This approach demonstrates a balanced, risk-based CI/CD security model focused on prevention, visibility, and traceability.

