# Personal GitHub Pages site

Static files for the account owner's personal Tesla Fleet API public key.

## Paths

- Public key: `/.well-known/appspecific/com.tesla.3p.public-key.pem`
- OAuth callback explanation: `/oauth/callback/`

SHA-256 of the public key file: `195b5f2d90a190928848ec5462e11346f8198f0840914c2387c6ca90ba4d654c`

Intended origin after this repository is named `fabriziogambardella-dotcom.github.io` and free GitHub Pages is enabled from the `main` branch at `/`:

- `https://fabriziogambardella-dotcom.github.io/`
- `https://fabriziogambardella-dotcom.github.io/.well-known/appspecific/com.tesla.3p.public-key.pem`
- `https://fabriziogambardella-dotcom.github.io/oauth/callback/`

Register the callback with the trailing slash. That URL is the static `oauth/callback/index.html` page.

## Security

Only the public EC P-256 key belongs here. Keep the private key on the coordinator's computer. Do not commit a private key, client secret, access token, refresh token, backup code, or vehicle data.

`.nojekyll` is present so GitHub Pages serves the `.well-known` directory.

The callback page does not read the query string, store it, or send it anywhere. Do not add scripts, analytics, forms, or token exchange to that page. The coordinator reads the result from the browser address bar.

GitHub still receives the callback request, including the query string, because the browser loads this hosted page. This site does not forward that request anywhere else.

## Publish

GitHub Pages for a user site serves the repository root on the default branch. After the change is on `main`:

1. Repository name: `fabriziogambardella-dotcom.github.io`
2. Settings → Pages → Build and deployment → Deploy from a branch
3. Branch `main`, folder `/ (root)`

Then confirm the live body matches this file exactly:

```sh
curl -fsS https://fabriziogambardella-dotcom.github.io/.well-known/appspecific/com.tesla.3p.public-key.pem | sha256sum
```
