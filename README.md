## Stage 3: Trivy Security Scan Results

| Metric | Before (fest-backend:0.1) | After (fest-backend:0.2) |
|---|---:|---:|
| CRITICAL Vulnerabilities | 234 | 0 |
| HIGH Vulnerabilities | 2249 | 49 |
| MEDIUM Vulnerabilities | 7530 | 64 |
| LOW Vulnerabilities | 3210 | 63 |
| UNKNOWN Vulnerabilities | 158 | 1 |
| Image Content Size | 412 MB | 47.9 MB |
| Image Disk Usage | 1.61 GB | 195 MB |

### Security Improvements

- Updated base image to `python:3.13-slim-trixie`.
- Upgraded Flask and Werkzeug dependencies.
- Configured the application to run as a non-root user (`appuser`).
- Trivy CRITICAL vulnerability check with `--ignore-unfixed` returned exit code `0`.
- Reduced image content size by approximately 88.4%.

## Stage 4: Docker Hub Publishing and Deployment

### Docker Hub Repository

- **Docker Hub Username:** `soumya0812`
- **Repository:** https://hub.docker.com/r/soumya0812/fest-backend
- **Published Tags:**
  - `soumya0812/fest-backend:1.0.0`
  - `soumya0812/fest-backend:1.0`

### Image Digest

`sha256:fdd50ee6e246b6906bd55adafdf013ff01d63091103448758b6a179d1982f592d`

### Deployment Verification

- Updated `compose.yaml` to use `soumya0812/fest-backend:1.0.0`.
- Pulled the published image from Docker Hub.
- Removed the previous local `fest-backend` images.
- Started the application using `docker compose up -d`.
- Verified that the backend health endpoint returned version `1.0.0`.
- Confirmed database connectivity.
- Confirmed existing registrations remained available after recreating the backend container.

