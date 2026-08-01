# Wilson Window Cleaning Services — website

The website for Wilson Window Cleaning Services, Hood River OR. Plain HTML and
CSS — no build step, no dependencies, no framework. Open `index.html` in a
browser and it works.

```
index.html          the main page
terms.html          Terms of Service, incl. SMS terms for A2P 10DLC
privacy.html        Privacy Policy, incl. the mobile-data clause carriers look for
assets/styles.css   all the styling (brand colours at the top)
assets/logo.webp    the full logo lockup
assets/logo-mark.png  just the squeegee, cropped from the lockup for the header
assets/photo-hero.jpg the hero image
```

## Replacing the hero photo

Drop a new file in at `assets/photo-hero.jpg` and update the `width` and
`height` attributes on the `<img>` in `index.html` to match — they prevent the
page jumping around while the image loads.

It's displayed as a 4:5 crop anchored on the centre, so a tall portrait photo
will lose roughly equal amounts off the top and bottom. Keep the subject away
from both edges. Save it at about 1200px wide and under ~300 KB.

## What's already filled in

Everything is in place — the site is ready to publish.

- Hero photo `assets/photo-hero.jpg`, cropped 4:5 and centre-anchored
- Booking link on all three "Book online" buttons
- Logo: `assets/logo-mark.png` in the header and as the favicon, full lockup as
  the social share image. Brand blue `#005aab` and cream `#fdfbf7` are sampled
  straight out of the logo file.
- Phone `(833) 696-4541` (Lead Connector), email `alexwilson112009@gmail.com`
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

## A2P 10DLC registration

`terms.html` and `privacy.html` exist so the messaging campaign can be
registered and verified. When the registration form asks for URLs, give it:

| Field | URL |
| --- | --- |
| Privacy policy | `https://wilsonwindowcleaning.us/privacy.html` |
| Terms & conditions | `https://wilsonwindowcleaning.us/terms.html` |

Both are linked in the footer of every page, which is where reviewers look
first.

What's covered, because carriers check for each of these specifically:

- Program description — the exact message types that get sent
- How consent is collected, and that numbers are never bought or rented
- "Message frequency varies"
- "Message and data rates may apply"
- STOP to opt out, START to opt back in, HELP for help
- Customer care phone and email
- Carriers are not liable for delayed or undelivered messages
- Consent is **not** a condition of purchase
- The mobile-information clause in the privacy policy stating opt-in data is
  never shared with third parties or affiliates for marketing

**These are templates, not legal advice.** Read both pages and make sure every
statement is actually true of how you operate before submitting them — the
3-day satisfaction window, the message types, and the payment terms are the
ones most likely to need adjusting.

**The consent checkbox has to live on the booking form itself.** These pages
describe consent; they cannot collect it. In Lead Connector, add an unchecked
opt-in checkbox to the booking form with wording along these lines:

> I agree to receive text messages from Wilson Window Cleaning Services about
> my quote and appointments. Message frequency varies. Message and data rates
> may apply. Reply STOP to opt out or HELP for help. See our
> [Privacy Policy](https://wilsonwindowcleaning.us/privacy.html) and
> [Terms](https://wilsonwindowcleaning.us/terms.html).

It must default to unchecked and must not be required to submit the form.
Registration usually asks for a screenshot of it.

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
