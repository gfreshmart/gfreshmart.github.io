# Deployment notes

## Live preview (GitHub Pages)

Served from the `claude/laughing-lovelace-8pys06` branch:

- **Mahakal Supermart, Bijoliya** — the working store page template:
  https://gfreshmart.github.io/store-page/franchise-stores/bijoliya-mahakal-supermart/
- Repo root (existing careers page):
  https://gfreshmart.github.io/store-page/

This is a **preview/staging deploy**, not the official site. Once this page is finished it
becomes the template every other store page is generated from.

### Before moving this page to www.gfreshmart.com

1. In `franchise-stores/bijoliya-mahakal-supermart/index.html`, change the robots meta back
   to `<meta name="robots" content="index, follow">` and delete the preview comment above it.
   It is set to `noindex, nofollow` so the GitHub Pages copy does not compete with
   gfreshmart.com in search results.
2. Delete the yellow "Draft page" bar (one `<div class="draft-bar">` below the header).
3. Replace the photo placeholders with real store photographs. Each gallery entry in the
   `PHOTOS` array takes `src:'img/<file>'`; entries without a `src` keep the placeholder.
4. Replace the video facade with the real YouTube/Vimeo embed, and the map placeholder with
   the Google Maps iframe.
5. Point the enquiry form at the CRM endpoint. The hidden `source_store` field carries
   `store_bijoliya_mahakal_supermart` for lead attribution.
6. The `canonical`, Open Graph and JSON-LD URLs already point at
   `https://www.gfreshmart.com/franchise-stores/bijoliya-mahakal-supermart` — no change needed.

The two logo files load from `gfreshmart.com/static-assets/images/`. If that host blocks
hotlinking from github.io, the page falls back to a styled "G-Fresh Mart" wordmark
automatically; on gfreshmart.com itself the real logos load.

## Mahakal Supermart, Bijoliya — content still to collect

Confirmed: store name (Mahakal Supermart), owner (Piyush), city/state/pincode
(Bijoliya, Rajasthan, 311602), 1,100 sq ft, approx. ₹25 lakh total investment,
green store theme.

Outstanding, each marked on the page itself:

- Store photographs (8 slots; captions already written)
- Owner's written testimonial and portrait photograph
- Owner's video testimonial
- Timeline: enquiry → site → agreement → fit-out → training → stocking → opening
- Opening date, days to open, products stocked, team size, opening hours
- Street address, store phone, Google Maps link
- Investment breakdown by component, and whether ₹25 lakh includes rent, deposit and
  working capital

Nothing on this page is invented — every unconfirmed field says "to be added".

## History

A template demo page for a fictional store (Vijay Nagar, Indore) was removed on
2026-10-21 now that a real store page exists. It is still in git history if the
fictional-content version is ever needed for reference:
`git show 09bfb76:franchise-stores/indore-vijay-nagar/index.html`
