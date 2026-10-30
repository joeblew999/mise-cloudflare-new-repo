# mise-cloudflare-new-repo

A Cloudflare Worker, with [mise-cloudflare](https://github.com/joeblew999/mise-cloudflare).

```sh
mise run cloudflare
```

shows what's done and what to run next. Everything else is in
[docs/mise-cloudflare/README.md](docs/mise-cloudflare/README.md).

It deploys on every push: production from `main`, and a preview for every pull request.

Every step says what it did and what to run next: mise run cloudflare.
