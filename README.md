# mjsauro.github.io

This repo backs the GitHub Pages user site at <https://mjsauro.github.io>. It no
longer hosts the portfolio itself — it redirects to the current one:

**<https://d12uot6ivwmo30.cloudfront.net/>** (source: [mjsauro/portfolio](https://github.com/mjsauro/portfolio))

## Layout

| Path         | Purpose                                                              |
| ------------ | -------------------------------------------------------------------- |
| `index.html` | Redirect to the current portfolio (meta refresh + JS, with a manual link as fallback) |
| `404.html`   | Same redirect, so any stale deep link lands on the new site rather than a bare 404 |
| `archive/`   | The original 2020 portfolio, still browsable at <https://mjsauro.github.io/archive/> |

The pre-redirect state of this repo is tagged **`v1-original-site`**:

```sh
git checkout v1-original-site
```

## Why a redirect instead of DNS

The new site is on CloudFront, but GitHub controls the `github.io` DNS zone, so
`mjsauro.github.io` can't be pointed at the distribution — no CNAME, and no way
to serve the ACM validation record a custom-domain cert would need. A
client-side redirect from this repo is the only option.

## Changing the redirect target

If the portfolio ever moves again (a custom domain, say), update the URL in
`index.html`, `404.html`, and the canonical/banner links in
`archive/index.html`. Pages rebuilds on push to `develop`.
