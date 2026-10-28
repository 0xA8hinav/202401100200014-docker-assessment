# 202401100200014-docker-assessment

FestPass three-tier app: frontend (nginx), backend (Flask), db (postgres).

- Name: Abhinav
- REGNO: 202401100200014
- PORT: 8014
- Docker Hub username: 0xabhinav
- Docker Hub repository: https://hub.docker.com/r/0xabhinav/fest-backend
- Digest of 1.0.0: sha256:5d7aaaf1ed43e4281b272c9a3f5a362bb33c76f40465af5b60d969299140210a

## Vulnerability report (Trivy)

| Image | Size | CRITICAL | HIGH |
| :--- | :--- | :---: | :---: |
| fest-backend:0.1 (before) | 1.61GB | 234 | 2249 |
| fest-backend:0.2 (after) | 228MB | 2 (0 fixable) | 59 |

- Before: `Total: 13357 (UNKNOWN: 158, LOW: 3206, MEDIUM: 7516, HIGH: 2243, CRITICAL: 234)` + python `Total: 24 (HIGH: 6, CRITICAL: 0)`
- After: `Total: 270 (HIGH: 59, CRITICAL: 2)` + python `Total: 6 (HIGH: 0, CRITICAL: 0)`
- Fix: `FROM python:3.12-slim-bookworm` (pinned), non-root `appuser`, upgraded to `Flask==3.1.3 Werkzeug==3.1.9 psycopg2-binary==2.9.13`
- Check: `trivy image --severity CRITICAL --ignore-unfixed --exit-code 1 fest-backend:0.2` exits 0

## Incomplete steps

- None yet
