# kendra-setu-keepalive

Keeps the hosted GCTMS backend awake.

- Target: https://kendra-setu-api.onrender.com/health
- Schedule: every 5 minutes (GitHub Actions cron)
- The Render free instance sleeps after ~15 minutes without traffic, so this job
  sends a request often enough to keep it warm.
- Once per day the job writes `last-ping.txt` so the repository stays active and
  GitHub does not disable the scheduled workflow after 60 days of inactivity.

No secrets are stored in this repository.
