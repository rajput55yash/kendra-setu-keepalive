# kendra-setu-keepalive

Keeps the hosted GCTMS (Kendra Setu) backend awake so sign-in stays fast.

- Target: https://kendra-setu-api.onrender.com/health
- Primary pinger: Cronitor check `kendra-setu-api-health`, every 5 minutes.
- The Render free instance sleeps after ~15 minutes without traffic, so a request
  every 5 minutes keeps it warm and login stays under ~1 second.

## Why the GitHub Actions schedule was removed

GitHub throttles `schedule` workflows on free plans: a `*/5 * * * *` cron ran only
every 3-6 hours in practice, which is why the API kept falling asleep. The workflow
is kept for manual runs only (`workflow_dispatch`), as a backup.

No secrets are stored in this repository.
