# mise-cloudflare-new-repo

**The problem.** You can read how [mise-cloudflare](https://github.com/joeblew999/mise-cloudflare) makes a new repo
into a Cloudflare Worker that deploys itself, but not see one: what is in the repo after `init` and the template, how
little of it is the Worker's own, and what GitHub and Cloudflare show once it's connected, a pull request's checks and
its preview, production from `main`. mise-cloudflare's own walks make their new repos in folders that are gone when
the walk ends.

**What mise-cloudflare-new-repo does.** It is such a new repo, made as mise-cloudflare's docs say and kept on GitHub:
`mise-cloudflare init`, which wrote mise-cloudflare's files (`.mise/`, `.github/workflows/cloudflare.yml`, `.claude/`,
`docs/mise-cloudflare/`, `.gitignore`), then `mise run cloudflare:template`, which wrote the template's Worker
(`src/worker.js`, one request that touches D1, KV, R2 and a secret; `wrangler.jsonc`; `package.json` and its lockfile;
`.dev.vars.example`; the `mise.toml` that installs its wrangler). On 2026-10-30 it was deployed and connected to
Cloudflare's Workers Builds, which built a preview for every pull request and production from `main`. The Worker is
no longer on Cloudflare (2026-11-07), so for now a push is only checked (`mise run cloudflare:verify`, in
`.github/workflows/cloudflare.yml`), and nothing deploys until `mise run cloudflare:08-deploy` and
`mise run cloudflare:09-connect-github` are run again.

```sh
mise run cloudflare
```

shows what's done and what to run next. Everything else is in
[docs/mise-cloudflare/README.md](docs/mise-cloudflare/README.md).
