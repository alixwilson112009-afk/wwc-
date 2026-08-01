# Wilson Window Cleaning Services — website

The website for Wilson Window Cleaning Services, Hood River OR. Plain HTML and
CSS — no build step, no dependencies, no framework. Open `index.html` in a
browser and it works.

```
index.html          the whole page
assets/styles.css   all the styling (brand colours at the top)
assets/             the hero photo and logo go here (see below)
```

## Still to do

Two things before this goes live.

### 1. Add the hero photo

One photo is used on the page — the one in the hero, beside the headline. Save
it into `assets/` with this exact name:

| File | Which photo |
| --- | --- |
| `assets/photo-hero.jpg` | You cleaning the kitchen window from the garden bed |

Resize it to roughly 1600px on the long edge and under ~400 KB. Anything much
bigger makes the page slow on a phone, which is where most people will see it.

It's cropped to 4:5 and anchored on the center, so keep the subject away from
the very top and bottom edges.

### 2. Add the logo

The header mark and the favicon are currently inline SVG recreations of the
Wilson squeegee logo — close, but not your actual artwork. To use the real
file, save it as `assets/logo.png` and replace the `<svg class="brand-mark">`
block in the header with:

```html
<img class="brand-mark" src="assets/logo.png" alt="">
```

## What's already filled in

- Booking link on all three "Book online" buttons
- Phone `(509) 774-7789`, email `alexwilson112009@gmail.com`
- Hood River / White Salmon / Gorge service area
- Two years in business, 100+ customers
- Four real Nextdoor recommendations, shown with initials the way Nextdoor
  displays them, and a link back to the Nextdoor page

**Keep the review section honest.** Those four quotes are real ones from your
Nextdoor page. If you ever edit them, only ever paste in things customers
actually wrote — invented testimonials are illegal advertising in the US, and
the FTC has gone after small businesses for exactly that.

Same goes for the trust bar figures: "2 years" and "100+ customers" should stay
true as time passes. There are deliberately **no licensing, bonding or
insurance claims anywhere on the site** — don't add any unless they're accurate
and you can back them up.

## Change the colours

Everything visual comes from a handful of variables at the top of
`assets/styles.css`:

```css
:root {
  --brand: #1560bd;       /* buttons, links, accents — from the logo */
  --brand-dark: #114e99;  /* button hover */
  --brand-tint: #e9f1fa;  /* hero wash, booking band */
  --cream: #faf7f0;       /* the logo background cream */
}
```

Change `--brand` and the whole page follows.

## Publish it

### GitHub Pages

1. Push this repo to GitHub.
2. **Settings → Pages**.
3. Under **Source**, choose **Deploy from a branch**, then `main` and `/ (root)`.
4. Save. It goes live at `https://<username>.github.io/<repo>/` within a minute
   or two.

### Your own domain

You already own `wilsonwindowcleaning.us`. To point it here:

1. **Settings → Pages → Custom domain**, enter `wilsonwindowcleaning.us`, save.
   That writes a `CNAME` file into the repo.
2. At your domain registrar, add these DNS records:
   - Four `A` records for the apex `@`: `185.199.108.153`, `185.199.109.153`,
     `185.199.110.153`, `185.199.111.153`
   - One `CNAME` for `www` pointing at `<username>.github.io`
3. Back on the Pages settings, tick **Enforce HTTPS** once the certificate has
   been issued (usually well under an hour).

## Checking your work

Open `index.html` in a browser, or serve it locally:

```bash
python3 -m http.server 8000
```

Then visit http://localhost:8000. Before going live, check nothing was missed:

```bash
ls assets/photo-hero.jpg   # the hero photo must exist
```
