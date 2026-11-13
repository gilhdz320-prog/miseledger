# Proof — landing

Static page. No build step, no dependencies.

- `index.html` — the whole page
- `img/` — hero, the four walk photos, and the three card images (see `img/SHOT-LIST.md`)
- `og.png` — the card that appears when the link is shared (1200×630)

## Run locally

```bash
python3 -m http.server 8081
# http://localhost:8081
```

## Deploy

The repository deploys as a static site on Vercel:

1. Push this folder to GitHub (`proof-landing`).
2. Vercel → **Add New → Project** → import the repository.
3. Framework preset: **Other**. No build command, output directory: **`.`**
4. **Settings → Domains → Add** `proof.kitchen` and `www.proof.kitchen`.

## Domain: how `proof.kitchen` serves this page

At the registrar (where the domain was bought), point DNS at Vercel:

- Option A (recommended): change the **nameservers** to `ns1.vercel-dns.com` and
  `ns2.vercel-dns.com`. Vercel then manages every record.
- Option B: keep the registrar's DNS and add `A 76.76.21.21` for the root, and
  `CNAME cname.vercel-dns.com` for `www`.

Propagation takes minutes to a few hours. Vercel issues the TLS certificate
automatically.

## Subdomain for the app

The product stays where it is (`teaching-kitchen-os.vercel.app`). When you want it under
the same brand, add `app.proof.kitchen` as a domain to the product project on Vercel and
a `CNAME` pointing to `cname.vercel-dns.com`. Same file, different project.
