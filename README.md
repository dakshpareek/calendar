# Calendar

A minimal monthly calendar. Single HTML file, no build step, no dependencies. Auto-detects today, respects system dark mode, prints cleanly.

## Run locally

Open `index.html` in any browser. That's it.

## Deploy to GitHub Pages

1. Create a new GitHub repository.
2. Upload `index.html` and `.nojekyll` to the repo root and commit.
3. Go to **Settings → Pages**.
4. Under **Source**, choose **Deploy from a branch**, pick `main` and `/ (root)`, then save.
5. Within a minute the site is live at `https://<username>.github.io/<repo-name>/`.

**Tip:** if you name the repo exactly `<username>.github.io`, it serves at `https://<username>.github.io/` with no subpath — cleaner URL, recommended.

## Use a custom domain

1. In the repo root, create a file named `CNAME` (no extension). Put your domain on a single line — for example:

   ```
   calendar.example.com
   ```

2. Configure DNS with your registrar:

   **Subdomain** (`calendar.example.com`, `www.example.com`, etc.) — add a `CNAME` record:

   | Type  | Name      | Value                       |
   |-------|-----------|-----------------------------|
   | CNAME | calendar  | `<username>.github.io`      |

   **Apex domain** (`example.com` with no subdomain) — add four `A` records pointing to GitHub Pages, all with name `@`:

   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```

   Optionally also add `AAAA` records for IPv6:

   ```
   2606:50c0:8000::153
   2606:50c0:8001::153
   2606:50c0:8002::153
   2606:50c0:8003::153
   ```

3. Back in **Settings → Pages**, enter your domain under **Custom domain** and save. Once DNS resolves, tick **Enforce HTTPS** — GitHub provisions a Let's Encrypt certificate automatically (can take a few minutes).

DNS propagation can take up to 24 hours but is usually faster. Use `dig your-domain.com` from the terminal to verify.

## Keyboard shortcuts

- `←` / `→`: previous / next month
- `T`: jump to today

## Customizing

All colors live as CSS variables at the top of the `<style>` block in `index.html`:

- `--page-bg` — page background outside the card
- `--card-bg` — the calendar card itself
- `--ink` — main number color
- `--accent` — month name year, nav buttons, weekday labels
- `--strip` — the weekend column background
- `--strip-ink` — number color inside the weekend strip
- `--today-bg` / `--today-fg` — the highlighted "today" box

Light and dark modes have their own values — edit both blocks if you change colors. The serif font uses a system stack (Iowan Old Style → Palatino → Georgia); to swap in a custom face, add a `@font-face` rule and update `--serif`.

## License

MIT — do whatever you want with it.
