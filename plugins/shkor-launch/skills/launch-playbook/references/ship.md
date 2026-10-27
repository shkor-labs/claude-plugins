# Steps 2–3. Project, repo, public URL

## 2. Project and repo

1. `project_create` with `name`, a 1–2 sentence `description` (the promise from
   `LAUNCH.md`), and `revenue_pct`. That's the studio's share of revenue that comes in
   through the studio checkout, from 10 to 100%, held automatically from each payment.
   Tell the user the number and get their agreement before calling. The share is
   part of their plan terms, so don't pick it for them.
2. `git_repo_create` with a short slug (latin letters, digits, hyphens). It returns a clone
   URL with an embedded token. Add it as a remote **without printing it back**:
   `git remote add shkor <url>` then `git push shkor HEAD:main`.
   Make sure `.env`, keys and `node_modules` are in `.gitignore` before the first push.

## 3. Public URL

`site_request` proxies `https://<slug>.cil.by` to a port on the user's Shkor workspace
server (default 8099). It does not host files itself.

Checklist before calling it:

- The app runs on the **workspace server**, not on the user's laptop. If they develop
  locally, pull the repo on the server first.
- It listens on `0.0.0.0:<port>`, not `127.0.0.1`.
- The port is open: `ufw allow <port>/tcp`.
- It runs under a process manager so it survives logout and reboot: a systemd
  unit, `pm2`, or `docker run --restart unless-stopped`.

After the call, the first request may return 500 or time out for ~15 s while TLS is
issued. Retry before debugging. Next.js SSR behind the proxy is handled by the
proxy template.

The plan includes a limited number of subdomains, so reuse a slug rather than
requesting a new one per experiment.

Done when `curl -sI https://<slug>.cil.by` returns 200 and the page shows the promise
from `LAUNCH.md` above the fold.
