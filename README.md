# Daniel M. Thompson's website

The existing single-page website, prepared for free hosting on GitHub Pages.

- Preview: https://danmckinleythompson.github.io/website/
- Production domain: https://danmthompson.com/
- Pages settings: https://github.com/danmckinleythompson/website/settings/pages

## Contents

`index.html` comes from the live website downloaded on September 6, 2026. It
preserves the current text, layout, font, and Google Analytics configuration,
including the Associate Professor title. The hosting-specific GoDaddy monitoring
scripts were removed; they do not affect the page's appearance.

`papers/` contains all 22 PDFs linked from that homepage: the CV, publications,
appendices, working papers, and the March 2025 correction note. Filenames and
paths are unchanged so the existing PDF URLs can continue working after the
domain moves.

The public server does not list the contents of its `papers/` directory and has
no sitemap, so this is a copy of all PDFs linked from the current homepage, not
a complete server backup. Six additional PDF URLs in the older local homepage
were checked; they already return 404 on the current server.

## Update the website

Edit `index.html` or replace/add PDFs in `papers/`, then commit and push to `main`.
GitHub Pages publishes the repository root automatically. There is no package
installation or build command; `.nojekyll` keeps the files as plain static files.

The repository's `.gitignore` allows only the homepage, PDFs, and configuration
files. To add images or other assets later, explicitly allow their paths there.
Local credentials, backups, and unused assets are not part of this repository.

For a local preview, run `python3 -m http.server 8000` from a clean clone of this
repository, then visit http://localhost:8000/.

## Connect danmthompson.com

The GitHub preview can be tested before changing the live domain. Complete these
steps when ready to move traffic from GoDaddy:

1. In your GitHub account's [Pages settings](https://github.com/settings/pages),
   add `danmthompson.com` as a verified domain. Add the DNS TXT record GitHub
   provides in GoDaddy's DNS settings, then finish verification in GitHub. Keep
   that TXT record.
2. In this repository's **Settings → Pages**, set **Custom domain** to
   `danmthompson.com` and save. Do this before changing the website's DNS records.
   GitHub will create a `CNAME` file on `main`; pull that commit into your local
   checkout before making your next update.
3. In GoDaddy's DNS settings, replace the website's existing apex (`@`) A records
   with the four A records below. Replace the `www` record with the CNAME below.
   Replace or remove old website AAAA records pointing to GoDaddy; optional
   GitHub IPv6 values are in the linked documentation. Keep your nameservers,
   email MX records, and unrelated DNS records as they are.

   | Type | Name | Value |
   | --- | --- | --- |
   | A | `@` | `185.199.108.153` |
   | A | `@` | `185.199.109.153` |
   | A | `@` | `185.199.110.153` |
   | A | `@` | `185.199.111.153` |
   | CNAME | `www` | `danmckinleythompson.github.io` |

4. Allow DNS and the HTTPS certificate to finish updating; GitHub says each can
   take up to 24 hours. Enable **Enforce HTTPS** when available. Check the
   homepage, `www` redirect, CV, and paper links at your domain.
5. Once those checks pass, turn off renewal of the GoDaddy web-hosting product.
   Retain domain registration and any email service you use. Check whether the
   products are bundled before canceling a bundle.

GitHub instructions: [publish from a branch](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site),
[verify a domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages),
[configure domain DNS](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site).
