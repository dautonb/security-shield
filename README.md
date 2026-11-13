# rdx-cron

Public repository that does one thing: every 15 minutes it calls `POST /v1/internal/cycle` on the
Rug-Pull Shield API so the cached security feed stays fresh. It contains no application code.

Why a separate repo: GitHub Actions minutes are unlimited for public repositories, so the 15-minute
schedule costs nothing, while the API code itself can live in a private GitLab/GitHub repository.

## Setup
1. Settings > Secrets and variables > Actions > **Secrets** > New repository secret: `CRON_SECRET`
   (must equal the `CRON_SECRET` set on Vercel).
2. Optional, **Variables** tab: `SERVICE_URL` if the API is not served from `https://rdxdata.xyz`.
3. Actions > Refresh Security Feed > Run workflow, and check the log shows `HTTP 200`.

Never put secrets in this repository: its code and logs are public.
