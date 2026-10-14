# Berry Labs website

A single static page (`index.html`). There's no build step and no other assets. Fonts load from Google Fonts.

## Deploying to our GoDaddy domain

### If the domain has GoDaddy Web Hosting (cPanel)
1. In GoDaddy, go to **Web Hosting**, click **Manage**, then **cPanel Admin**, then **File Manager**, and open `public_html/`.
2. Remove or rename any existing `index.html` or placeholder page.
3. **Upload** `index.html`.
4. For HTTPS, go to cPanel, then **SSL/TLS Status**, then **Run AutoSSL**.

### If the domain has no hosting (domain only or Website Builder)
Host the file on Netlify and point DNS at it:
1. Deploy with the Netlify CLI (`npx netlify-cli deploy --prod --dir .`) or drag this folder onto https://app.netlify.com/drop.
2. In Netlify, go to **Domain management** and add the domain.
3. In GoDaddy, go to the domain's **DNS**, then **DNS Records**:
   - `A` record: name `@`, value `75.2.60.5`
   - `CNAME` record: name `www`, value `<site-name>.netlify.app`
   - Delete any existing `A @` record (parking or Website Builder) first.
4. Wait for DNS to propagate (minutes to an hour). Netlify then provisions HTTPS automatically.

## Updating the site
Edit `index.html`, commit, and repeat the upload (cPanel) or the deploy (Netlify).
