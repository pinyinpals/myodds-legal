# myodds-legal

Static site for [myodds.app](https://myodds.app):

- Landing page (`index.html`)
- Privacy policy (`/privacy/`)
- Terms of service (`/terms/`)
- Apple App Site Association file for Universal Links (`/.well-known/apple-app-site-association`)

## Hosted on GitHub Pages

Pages serves directly from the `main` branch root. Custom domain `myodds.app`
goes in `CNAME` (currently absent — add when the domain is purchased).

## When you buy `myodds.app`

1. Cloudflare → DNS: add `CNAME myodds.app → pinyinpals.github.io` (DNS only)
2. Repo Settings → Pages: set Custom domain to `myodds.app`
3. Create a `CNAME` file in this repo with one line:
   ```
   myodds.app
   ```
4. Verify HTTPS auto-issues (~5 min)
5. Confirm:
   ```bash
   curl -sI https://myodds.app/.well-known/apple-app-site-association
   # Should be 200 OK, content-type: application/json
   ```
6. In iOS project, re-enable the `applinks:myodds.app` associated-domains
   entitlement (currently commented out in `oddsgpt/project.yml`)

Until then, the in-app share text uses the custom URL scheme `myodds://join/CODE`
which works without any domain.

## Editing

Plain HTML + inline CSS, no build step. Commit and push, GitHub Pages rebuilds
in ~30s.
