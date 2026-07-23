# Merkhet Ventures website

This folder is the deployable public website.

## Cloudflare Pages target

Configure the Cloudflare Pages project to use this folder as its root directory. The site is static: no framework or server runtime is required.

The deployment output must contain this folder's `index.html` at its root. Keep the custom domain configuration in Cloudflare Pages and Cloudflare DNS; do not add a GitHub Pages `CNAME` file here.
