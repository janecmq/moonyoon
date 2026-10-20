# moonyoon

Static sites hosted on [moonyoon.com](https://moonyoon.com) via GitHub Pages.

## Add a site

1. Create a folder in `sites/`, e.g. `sites/my-site/`
2. Put an `index.html` (plus any CSS, JS, images) inside it
3. Push to `main`

It goes live at `https://moonyoon.com/my-site/` in about a minute.

- `sites/index.html` is the homepage (moonyoon.com)
- Use relative links inside a site (`style.css`, not `/style.css`)
- Deploys run from `.github/workflows/deploy.yml`; check progress in the Actions tab

## One-off setup

### Namecheap (Domain List > moonyoon.com > Manage > Advanced DNS)

Delete the default parking records, then add:

| Type  | Host | Value               |
|-------|------|---------------------|
| A     | @    | 185.199.108.153     |
| A     | @    | 185.199.109.153     |
| A     | @    | 185.199.110.153     |
| A     | @    | 185.199.111.153     |
| CNAME | www  | janecmq.github.io.  |

### GitHub (repo Settings > Pages)

1. Source: **GitHub Actions**
2. Custom domain: `moonyoon.com`, then Save
3. Once the DNS check passes, tick **Enforce HTTPS**

### moonyoon.co (redirects to moonyoon.com)

GitHub Pages only serves one custom domain, so moonyoon.co forwards to moonyoon.com.

In Namecheap (Domain List > moonyoon.co > Manage > Advanced DNS), delete the default parking records, then add:

| Type         | Host | Value                  | Redirect type   |
|--------------|------|------------------------|-----------------|
| URL Redirect | @    | https://moonyoon.com/  | Permanent (301) |
| URL Redirect | www  | https://moonyoon.com/  | Permanent (301) |

Paths carry over, so `moonyoon.co/hello` lands on `moonyoon.com/hello`.
