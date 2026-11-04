# UDI home site

One-page static site for UDI (Ummatic Digital Infrastructure), live target `https://ummatic.digital`. It is a **pre-launch working draft**. Plain HTML and CSS, no build step, no JavaScript, no third-party requests.

```
public/            the whole deployable site (index.html, assets/)
wrangler.jsonc     Cloudflare Worker with static assets, serves ./public
LICENSE            MIT
```

## Preview locally

```
python -m http.server 8000 --directory public
```

Open http://localhost:8000/ and stop the server with Ctrl+C.

## Deploy to Cloudflare

The site is a Cloudflare Worker with static assets (no Worker script). Only `public/` is uploaded.

1. Do the pre-deploy gate below.
2. In your shell, set `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID`. Never write them into a file in this repo.
3. Check first: `npx wrangler@4.149.0 deploy --dry-run`
4. Deploy: `npx wrangler@4.149.0 deploy`

The route in `wrangler.jsonc` attaches the custom domain `ummatic.digital`. Whether the token may attach it has not been tested; if it is refused, the site stays on its workers.dev address until the permission is fixed in the Cloudflare dashboard.

## Pre-deploy gate

Do not deploy until the `research` repository (`github.com/ummatic-udi/research`) is public and every outbound link on the page returns 200. Until then the source links 404.

## Licences

- Site code and content: MIT, see `LICENSE` ("UDI contributors" until the legal owner is decided).
- Montserrat fonts: SIL Open Font License 1.1, in `public/assets/fonts/OFL.txt`.
- Research diagrams and the UDI logo files come from the UDI research and branding folders; confirm their licence before deploy.

## Open decisions

- Legal owner of the copyright and the name.
- Whether `www.ummatic.digital` redirects to the apex.
- Whether to use a dedicated, narrower Cloudflare token for this site.
- Audience: every call to action is a GitHub link; a contact or newsletter route is deferred.
- The cloud figure says 63% (28%, 20%, 15%); the research note's prose says "about two-thirds" and may need correcting.
- Whether "UEP" keeps its expansion; if not, diagram 05 must be regenerated.
- The simple stack diagram is titled "five floors" but lists six; regenerate if that is a mistake.
