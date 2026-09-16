# AI Video Blueprint — Tutorial Landing Page

A short, single-page, no-build landing page for selling one digital tutorial. Plain HTML/CSS/JS in one file — no framework, no dependencies, nothing to install.

Six sections only: Hero → What you'll learn → Preview → Pricing → FAQ (4 questions) → Final CTA.

## Run it locally

You don't need to install anything. Pick one:

- **Easiest:** double-click `index.html` and it opens in your browser.
- **Recommended** (avoids minor browser quirks with fonts/paths): serve it locally.
  ```bash
  cd course-landing
  python3 -m http.server 8000
  ```
  Then open `http://localhost:8000` in your browser.

## Deploy it for free

Since it's a single static file, any static host works. A few good free options:

- **Netlify / Vercel / Cloudflare Pages:** drag the `course-landing` folder into their dashboard, or connect a GitHub repo — done in a couple of minutes.
- **GitHub Pages:** push this folder to a GitHub repo, enable Pages in the repo settings, point it at the branch. No build step needed.

## What to edit before launch

Everything you'll want to customize is marked with comments in `index.html`:

1. **Brand / product name** — currently set to "AI Video Blueprint". Search for that text to change it again (nav, hero footer, pricing panel, buy button labels).
2. **Copy** — the headline, "what you'll learn" list, and FAQ are placeholder text written for a "3D PS2-style AI video" tutorial. Adjust the wording to match your exact process if needed — the structure stays the same either way.
3. **Price** — currently set to "$19.99". Search for that text (it appears in the pricing panel and the sticky mobile bar) to change it. There's also a `data-price-usd="19.99"` attribute on the buy button for reference.
4. **Buy button → Stripe:** find `id="buy-button"` in the Pricing section. Its `href="#"` is a placeholder. When you're ready to accept payments, replace it with your Stripe Checkout / Payment Link URL, e.g.:
   ```html
   <a href="https://buy.stripe.com/your_payment_link" id="buy-button" class="btn btn-primary btn-block btn-lg">
   ```
   Once that's a real link, the small "payment isn't connected yet" JavaScript alert at the bottom of the file becomes irrelevant — you can leave it (it only fires on the placeholder `#` href) or delete that script block.
5. **Images/video** — the hero visual and the three preview thumbnails currently use CSS gradients as stand-ins (marked `<!-- IMAGE SLOT -->` in the HTML) so the page loads instantly with no missing-image icons. Replace them with real example clips, thumbnails, or an embedded video (a YouTube/Vimeo iframe, or an `<img>`/`<video>` tag) whenever you have that media.
6. **Colors** — all colors are CSS variables at the top of the `<style>` block under `:root`. Change `--accent` and the rest there to re-skin the whole page in one place.
7. **Footer links** (Terms, Privacy, Refund policy) — currently plain text placeholders. Turn them into real links once you have those pages.

## Notes on what's intentionally NOT included

Per the brief, this is front-end only:
- No payment processing, no database, no accounts/auth, no backend.
- The buy button is a plain link, ready to be pointed at a Stripe Checkout / Payment Link URL later.
- No build tools, bundlers, or JS frameworks — just HTML/CSS/vanilla JS, so it's easy to host anywhere for free and easy to hand off to any developer later.
