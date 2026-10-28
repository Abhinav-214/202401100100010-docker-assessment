# CA-2 Practical Assessment: Docker & Container Security

### 1. Student & Service Information
- **Name:** Abhinav Verma
- **Class:** CS - A
- **Registration Number:** 202401100100010
- **Assigned Port:** 8010 (calculated using rule: 80 + last 2 digits of REGNO -> 80 + 10 = 8010)
- **Docker Hub Username:** abhinav7788
- **Docker Hub Link:** https://hub.docker.com/r/abhinav7788/fest-backend

---

### 2. AI Tools Declaration
Used Google Gemini and ChatGPT to help format Docker Compose files with multi-network isolation, construct hardened minimal Alpine Dockerfile, verify Trivy scanner flags, and execute cosign keypair generation and verification.

---

### 3. Backend Image Digest (v1.0.0)
`sha256:2366fce00e8d89fd155b06c7999abc1c8b4f946fdba74b55e1a0b5e18d34cd0a`

---

### 4. Vulnerability Remediation Table (Stage 3.3)

| Metric | fest-backend:0.1 (Base: python:3.9) | fest-backend:0.2 (Hardened: python:3.12.16-alpine) |
| :--- | :--- | :--- |
| **CRITICAL Vulnerabilities** | 234 | 0 |
| **HIGH Vulnerabilities** | 2243 | 0 |
| **Final Image Size** | ~1.61 GB | ~93.3 MB |

**Summary of fixes made:**
1. Switched the base image from bloated `python:3.9` to lightweight `python:3.12.16-alpine` to eliminate hundreds of outdated OS packages.
2. Created a dedicated non-root user (`appuser` with `appgroup`) inside the Dockerfile instead of running the application container as root.
3. Updated dependencies in `requirements.txt` to current secure versions (`Flask==3.1.2`, `Werkzeug==3.1.3`, `psycopg2-binary==2.9.10`).
4. Verified that running `trivy image --severity CRITICAL --ignore-unfixed --exit-code 1 fest-backend:0.2` exits with code 0.

---

### 5. Incomplete Steps
None. All 5 stages were completed according to the assessment specifications.
