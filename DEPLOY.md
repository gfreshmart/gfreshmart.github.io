# Mahakal Supermart — store page template (development)

A standalone store profile page, built as the template for G Fresh Mart store pages.
Nothing here is wired to the live site: no links, canonical tags or schema URLs pointing at
a production domain. The two exceptions are both asset loads, not site links: Google Fonts
for Poppins, and the official G Fresh Mart logo files. Attach the logo files to the repo
under `bijoliya-mahakal-supermart/img/` to remove the last external reference — the page
already falls back to a text wordmark if they fail to load.

## Live preview

https://gfreshmart.github.io/bijoliya-mahakal-supermart/

Served by GitHub Pages from the `claude/laughing-lovelace-8pys06` branch of
`gfreshmart/gfreshmart.github.io`, root folder.

The page carries `<meta name="robots" content="noindex, nofollow">` so a work-in-progress
template does not get indexed.

## Files

| Path | What it is |
|---|---|
| `bijoliya-mahakal-supermart/index.html` | The store page. All CSS and JS are inline — one self-contained file. |
| `bijoliya-mahakal-supermart/img/` | Store photographs go here. |
| `index.html` | An unrelated careers page that was already in the repo. Serves at the site root. |
| `franchise-store-page-structure.md` | The section-by-section spec this page was built from. |

## Store data on the page

Confirmed: store name (Mahakal Supermart), owner (Piyush), Bijoliya, Rajasthan, 311602,
1,100 sq ft, approx. ₹25 lakh total investment, green store theme.

Still to collect, each marked on the page itself as "to be added":

- Store tour video for the hero (a dummy video is embedded for now)
- Store photographs (8 gallery slots; captions already written)
- Owner's written testimonial and portrait photograph
- Owner's video testimonial
- Timeline: enquiry → site → agreement → fit-out → training → stocking → opening
- Opening date, days to open, products stocked, team size, opening hours
- Street address, store phone, map location
- Investment breakdown by component, and whether ₹25 lakh includes rent, deposit and
  working capital

Nothing on the page is invented — every unconfirmed field says so.

## Working on it

- **Store tour video:** the hero carries it. Change `data-video-id` on
  `<div class="hero-video">` to that store's YouTube id, and the poster image `src`
  to `https://i.ytimg.com/vi/<id>/maxresdefault.jpg`. The player is click-to-load, so
  YouTube is not contacted until a visitor presses play.
- **Photographs:** each entry in the `PHOTOS` array near the bottom of the file takes
  `src:'img/<file>'`. With a `src` it renders the real photograph; without one it keeps
  the placeholder frame, so photos can be added a few at a time.
- **Draft markers:** the dashed panels use `class="pending"` and come out as content gets
  filled in. The yellow draft bar and the breadcrumb were removed on request.
- **Placeholder links:** header, breadcrumb and footer links are `href="#"` on purpose.
  They are structure for the template, to be pointed somewhere when the template is adopted.
- **Enquiry form:** handled in JS with `preventDefault()` and shows a success state in place.
  The hidden `source_store` field carries `store_bijoliya_mahakal_supermart`.
