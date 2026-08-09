# mjsauro.github.io

This repo backs the GitHub Pages user site at <https://mjsauro.github.io>. It no
longer hosts the portfolio itself — it redirects to the current one:

**<https://mattsauro.com/>** (source: [mjsauro/portfolio](https://github.com/mjsauro/portfolio))

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

GitHub controls the `github.io` DNS zone, so `mjsauro.github.io` can't be
pointed anywhere else — a user site's hostname is fixed. A client-side redirect
from this repo is the only option.

Do **not** add a `CNAME` file here. That would claim `mattsauro.com` for GitHub
Pages and take it away from the CloudFront distribution that actually serves the
site.

## Changing the redirect target

If the portfolio ever moves again, update the URL in `index.html`, `404.html`,
and the canonical/banner links in `archive/index.html`. Pages rebuilds on push
to `develop`.
