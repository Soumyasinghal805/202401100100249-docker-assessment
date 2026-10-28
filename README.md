# Docker & Container Security Assessment

## 1. Student and Project Details

- **Name:** Soumya Singhal
- **Registration Number (REGNO):** 202401100100249
- **Application Port:** 129
- **Docker Hub Username:** soumya0812
- **Docker Hub Repository:** https://hub.docker.com/r/soumya0812/fest-backend

## 2. Project Overview

This project demonstrates backend containerization, multi-container orchestration using Docker Compose, vulnerability scanning with Trivy, publishing Docker images to Docker Hub, and image signing and verification using Cosign.

### Technologies Used

- Docker and Docker Compose
- Python and Flask
- PostgreSQL
- Nginx
- Trivy
- Docker Hub
- Cosign
- Git and GitHub

## 3. AI Tools Used

| AI Tool | Purpose |
|---|---|
| ChatGPT | Assistance with Docker commands, troubleshooting, security scanning, Cosign signing and verification, and README documentation. |

AI tools were used for guidance and troubleshooting. Commands were executed and results were checked in the project environment.

## 4. Docker Hub Image Details

**Repository:** `soumya0812/fest-backend`

Published tags:
- `1.0`
- `1.0.0`
- `1.0.1`

**Digest of image version 1.0.0:**

```text
sha256:fdd50ee6e246b6906bd55adafdf013ff01d63091103448758b6a179d1982f592d
```

The image was pushed to Docker Hub and deployed using Docker Compose.

## 5. Vulnerability Scan — Before and After

Trivy was used to scan the backend Docker image before and after security improvements.

| Severity | Before (fest-backend:0.1) | After (fest-backend:0.2) |
|---|---:|---:|
| Critical | 234 | 0 |
| High | 2249 | 49 |
| Medium | 7530 | 64 |
| Low | 3210 | 63 |
| Unknown | 158 | 1 |

### Security Improvements

- Updated the Python base image to `python:3.13-slim-trixie`.
- Updated Python package dependencies.
- Created a non-root application user.
- Ran the application as the non-root user.
- Re-scanned the updated image using Trivy.

**Result:** The updated image scan reported zero Critical vulnerabilities. Some High, Medium, Low and Unknown findings remained.

## 6. Docker Compose Deployment

The application uses Docker Compose to run the following services:

- **Backend:** Python Flask API
- **Database:** PostgreSQL
- **Frontend:** Nginx

The health endpoint was tested at:

```text
http://localhost:129/api/health
```

The health response confirmed that the database connection was working and the expected registration number was returned.

## 7. Image Signing and Verification with Cosign

Cosign was used to sign the published `1.0.0` image and verify its signature using the public key.

The private signing key (`cosign.key`) was excluded from Git using the following `.gitignore` entry:

```text
*.key
```

The public key (`cosign.pub`) was retained for signature verification.

An unsigned image (`1.0.1`) was also tested. Verification returned `no signatures found`, demonstrating that an image without a matching signature could not pass the signature verification check.

## 8. Screenshots and Evidence

Evidence screenshots for the assessment stages are stored in the [`screenshots`](screenshots/) folder.

Security scan reports are stored in the [`reports`](reports/) folder.

## 9. Incomplete Steps

All five assessment stages were worked on. No incomplete steps are being claimed here; any limitations or remaining findings are documented above.

