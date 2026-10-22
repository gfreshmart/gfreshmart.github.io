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

- Opening date, days to open, products stocked, team size

Nothing on the page is invented — every unconfirmed field says so.

## SEO

Everything that does not need the final domain is in place:

- Title (58 chars) and meta description (150 chars), both unique to this store
- One `<h1>`, a clean `<h2>` hierarchy beneath it, and a `<main>` landmark
- All 15 photographs are **in the HTML**, not injected by script, each with alt text and
  explicit width/height. Crawlers that do not run JavaScript still see them, and the
  dimensions stop the layout shifting as they load
- Below-the-fold images lazy-load; the hero poster is marked `fetchpriority="high"` as the
  likely LCP element
- JSON-LD: `GroceryStore` (name, description, photographs, address, area served, parent
  organization) and `FAQPage` whose five questions match the visible FAQ word for word
- Open Graph and Twitter card tags, including a share image
- `preconnect` to the font and video-thumbnail hosts

### Before launch

The page is deliberately `noindex, nofollow` while it lives on GitHub Pages, so this
staging copy never competes with the real one in search.

1. Delete the `robots` meta so the page can be indexed
2. In the `BEFORE LAUNCH` comment block in `<head>`, set the canonical and `og:url` to the
   page's real address and make `og:image` / `twitter:image` absolute
3. Add the page to the site's `sitemap.xml`
4. Point the header, footer and FAQ links at real pages — they are `href="#"` placeholders
   now, so the page passes no internal link equity

## Working on it

The store's exact street address, opening hours, phone number and map are deliberately not
on the page: visits are arranged through the franchise team instead.

- **Videos:** the hero carries a store tour and the owner section carries a testimonial. Change `data-video-id` on
  `<div class="hero-video">` to that store's YouTube id, and the poster image `src`
  to `https://i.ytimg.com/vi/<id>/maxresdefault.jpg` — on each `<div class="hero-video">`.
  Both players are click-to-load, so YouTube is not contacted until a visitor presses play.
- **Photographs:** the gallery is a uniform three-column grid — nine photographs make a
  tidy 3x3. Every tile is the same 16:9 size, so no photograph is a special case and the
  rows stay even whatever the count. Two columns under 900px, one under 560px.

  **Do not compress photographs before sending them.** Each one is stored at three widths
  (800, 1200 and 1600px), generated from the original, and the browser downloads only the
  width it needs. The grid tile displays at roughly 370px, so the 800px file is already
  sharp on a retina screen at around 60-85 KB; the 1600px file is only fetched when a
  visitor opens the lightbox. Squeezing a 2000px image under 100 KB throws away quality to
  pay for pixels nobody sees.

  To regenerate the variants after adding an original:
  ```python
  from PIL import Image
  im = Image.open('img/name.webp').convert('RGB')
  for w in (800, 1200):
      im.resize((w, round(im.height*w/im.width)), Image.LANCZOS) \
        .save(f'img/name-{w}.webp', 'WEBP', quality=82, method=6)
  ```
  Then add the figure to the grid:
  ```html
  <figure data-cat="groceries"><img src="img/name-800.webp"
          srcset="img/name-800.webp 800w, img/name-1200.webp 1200w, img/name.webp 1600w"
          sizes="(max-width:560px) 92vw, (max-width:900px) 46vw, 31vw"
          data-full="img/name.webp" alt="Grocery aisle"
          width="1600" height="900" loading="lazy" decoding="async"></figure>
  ```
  The alt text doubles as the lightbox caption. `data-cat` is optional: the filter buttons
  build themselves from whichever categories are used and disappear when none are.
- **Enquiry form:** handled in JS with `preventDefault()` and shows a success state in place.
  The hidden `source_store` field carries `store_bijoliya_mahakal_supermart`.
