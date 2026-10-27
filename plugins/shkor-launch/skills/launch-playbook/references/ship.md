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

Pick the path by what the product is.

### A. Static site or SPA: `site_publish` (no server needed)

Use this for landing pages and front-end-only apps: plain HTML, or a Vite,
React, Vue or Svelte build, or a Next.js `output: 'export'` build. Back-ends
such as Supabase or Firebase are fine because they're called from the browser.

1. Build locally (`npm run build`). Commit the build folder (`dist/`, `build/`,
   `out/` or `public/`) and push it to the repo from step 2. If the build folder
   is in `.gitignore`, remove that line, or publish from a separate `deploy`
   branch that contains only the build.
2. Make sure no secret is in the build. Anything in a front-end bundle is
   public, including `VITE_*` and `NEXT_PUBLIC_*` env vars. Only publishable
   keys belong there, such as the Supabase anon key or a Stripe publishable key.
3. Call `site_publish` with `slug`, `repo`, and optionally `ref` (default `main`)
   and `dir` (default: the first of `dist`, `build`, `out`, `public` or the
   root that has an `index.html`).
4. To update, push and call `site_publish` again with the same slug.

Dotfiles (`.env`, `.git`) and symlinks are never published. The limit is 100 MB
and 5000 files. For SPA client-side routes, use hash routing or generate one
HTML file per route, because unknown paths return 404.

### B. App with its own back-end: `site_request` (on the Shkor workspace server)

`site_request` proxies `https://<slug>.cil.by` to a port on the user's workspace
server (default 8099). This needs a plan that includes a server.

Checklist before calling it:

- The app runs on the **workspace server**, not on the user's laptop. Pull the
  repo onto the server.
- It listens on `0.0.0.0:<port>`, not `127.0.0.1`.
- The port is open: `ufw allow <port>/tcp`.
- It runs under a process manager so it survives logout and reboot: a systemd
  unit, `pm2`, or `docker run --restart unless-stopped`.

If there's no server and the product needs a back-end, say so plainly. The
options are to move the back-end logic to a hosted service (Supabase, Firebase)
and publish the front-end with path A, or to upgrade to a plan with a server.

### Both paths

The first request to a new subdomain may fail for ~15 s while TLS is issued.
Retry before debugging. The plan includes a limited number of subdomains, so
reuse a slug rather than creating one per experiment.

Done when `curl -sI https://<slug>.cil.by` returns 200 and the page shows the
promise from `LAUNCH.md` above the fold.
