# helm-sentinel

External, off-box uptime watchdog for the Helm VPS (77.42.37.42).

Runs on GitHub Actions (public repo = unlimited free minutes). Every 5 minutes
it opens a raw TCP connection to the VPS on port 443. After three failed checks
in a row it pages Barrie on Telegram as "Steve Jobs", and sends a recovery note
when the box answers again. It alerts only on a state change, not every run.

Why it exists: the on-box monitoring (Uptime Kuma, GlitchTip) cannot warn about
its own host going down. On 2026-06-28 a billing IP-block took the whole VPS
offline and nothing could page out. This watchdog lives entirely off the box and
on a channel that does not depend on it, so a total outage still reaches a phone.

No secrets live in this repo. The Telegram bot token and chat id are stored as
encrypted GitHub Actions secrets (TELEGRAM_JOBS_TOKEN, TELEGRAM_CHAT_ID).
