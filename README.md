# keep-alive

Keeps portfolio demos actually live:

- **Every 10 min:** pings P3 (testimonial-collector) on Render so it never cold-starts. Free tier gives 750 instance hrs/month; one always-on service uses ~720, so only P3 gets this. P2 sleeps on purpose.
- **Daily:** hits P3's public embed endpoint (runs a real DB query) and P2's Supabase REST API so neither free Supabase project pauses from 7 days of inactivity.
- **Weekly:** commits a timestamp so GitHub doesn't auto-disable the schedule after 60 days of repo inactivity.

## Setup required (one time)
Add two repo secrets (Settings → Secrets and variables → Actions):
- `P2_SUPABASE_URL` — proposal-generator Supabase Project URL
- `P2_SUPABASE_ANON` — its anon public key

Until these are set, the P2 step skips itself harmlessly.
