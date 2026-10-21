# Deployment notes

## Live preview (GitHub Pages)

The store profile page is served from GitHub Pages off the `claude/laughing-lovelace-8pys06` branch:

- Mahakal Supermart, Bijoliya (real store, content in progress):
  https://gfreshmart.github.io/store-page/franchise-stores/bijoliya-mahakal-supermart/
- Vijay Nagar, Indore (template demo, fictional content):
  https://gfreshmart.github.io/store-page/franchise-stores/indore-vijay-nagar/
- Repo root (existing careers page): https://gfreshmart.github.io/store-page/

This is a **preview/staging deploy**, not the official site.

### Before moving this page to www.gfreshmart.com

1. In `franchise-stores/indore-vijay-nagar/index.html`, change the robots meta back to
   `<meta name="robots" content="index, follow">` and delete the preview comment above it.
   It is set to `noindex, nofollow` so the GitHub Pages copy does not compete with
   gfreshmart.com in search results.
2. Replace the photo placeholders with real store photographs (see the captions for the
   required crop and subject of each one).
3. Replace the video facade with the real YouTube/Vimeo embed, and the map placeholder
   with the Google Maps iframe.
4. Point the enquiry form at the CRM endpoint. The hidden `source_store` field carries
   `store_indore_vijay_nagar` for lead attribution.
5. The `canonical`, Open Graph and JSON-LD URLs already point at
   `https://www.gfreshmart.com/franchise-stores/indore-vijay-nagar` — no change needed.

The two logo files load from `gfreshmart.com/static-assets/images/`. If that host blocks
hotlinking from github.io, the page falls back to a styled "G-Fresh Mart" wordmark
automatically; on gfreshmart.com itself the real logos load.

## Mahakal Supermart, Bijoliya — still to collect

Confirmed: store name, owner (Piyush), city/state/pincode, 1,100 sq ft, approx. ₹25 lakh
total investment, green store theme.

Outstanding, marked on the page itself:

- Store photographs (8 slots; captions are already written)
- Owner's written testimonial and portrait
- Owner's video testimonial
- Timeline: enquiry → site → agreement → fit-out → training → stocking → opening
- Opening date, days to open, products stocked, team size, opening hours
- Street address, store phone, Google Maps link
- Investment breakdown by component, and whether ₹25 lakh includes rent/deposit/working capital

The yellow "Draft page" bar below the header, and the dashed "To be added" panels, come out
as each item is filled in. Nothing on this page is invented — every empty field says so.
