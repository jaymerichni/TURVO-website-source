# TURVO website — source package

This folder contains the complete static TURVO website. It does not require a build step, database, framework, or server-side language.

## Files

- `index.html` — page structure and written content
- `styles.css` — colours, typography, layout, and responsive design
- `script.js` — navigation and small interface interactions
- `favicon.svg` — browser-tab icon
- `assets/` — project photographs, portraits, figures, and logos

Keep this structure unchanged when copying or uploading the website, because `index.html` uses relative paths to the other files.

## Run it locally

Opening `index.html` directly will usually work, but a small local web server gives the most accurate preview.

### macOS or Linux

1. Open Terminal.
2. Change into this folder:

   ```bash
   cd /path/to/TURVO-website-source
   ```

3. Start a local server:

   ```bash
   python3 -m http.server 8000
   ```

4. Open <http://localhost:8000> in a browser.
5. Press `Control+C` in Terminal to stop the server.

### Windows

1. Install Python from <https://www.python.org/downloads/> if it is not already installed. During installation, select **Add Python to PATH**.
2. Open PowerShell in this folder.
3. Run:

   ```powershell
   py -m http.server 8000
   ```

4. Open <http://localhost:8000> in a browser.
5. Press `Control+C` in PowerShell to stop the server.

## Edit the website

Use a plain-text or code editor such as Visual Studio Code.

- Edit wording and links in `index.html`.
- Edit visual styling in `styles.css`.
- Put new images in an appropriate folder inside `assets/`, then reference them with a relative path such as `assets/team/person-name.jpg`.
- Do not edit image files in a word processor.

Save the file and refresh the browser to see changes. Make a backup before large edits.

## Host it on a web server

Upload the **contents** of this folder to the web root used by your domain. Common web-root locations include `public_html`, `www`, or `/var/www/html`. The server must expose `index.html` at the root URL.

No installation or compilation is needed. Any normal static host or Apache/Nginx server can serve the files.

Example Nginx configuration:

```nginx
server {
    listen 80;
    server_name turvo.example.org;
    root /var/www/turvo;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

After placing the files in `/var/www/turvo`, test the Nginx configuration and reload Nginx. Configure HTTPS with your hosting provider or a certificate service such as Let's Encrypt before making the site public.

## Internet access

All photographs, figures, logos, CSS, and JavaScript are included locally. The page requests its typefaces from Google Fonts and contains outbound links to publications, profiles, ORCID records, and software repositories. Without internet access, the page remains readable using fallback fonts, but those external links and web fonts will not load.

## Updating the hosted copy

Replace the changed files on your server while preserving the same filenames and folders. If an update does not appear immediately, refresh the page without using the browser cache.
