# Build Brief — Fred's Gym NW3

Keep this compact. Add only sourced facts and assets actually used or deliberately rejected.

## Contact
- Email: nebile@me.com
- Email source URL: https://fredsnw3.com (homepage, rendered inside Nebile Cakir's trainer bio paragraph — not a general business inbox; this is the site's only contact address)
- Rechecked date: 2026-07-09 — recheck done by fetching https://fredsnw3.com directly and confirming `nebile@me.com` still appears verbatim in the page HTML (Nebile Cakir bio block).
- Phone: none used on site (see Do Not Claim — a personal mobile was found alongside the email but not authorized for use)
- Address: 24 Heath Street, Hampstead, London, NW3 6TE (source: https://fredsnw3.com/find-us and https://fredsnw3.com/join, both confirmed on recheck)

## Page Plan
- Scope: 3-page default (Home, Trainers, Contact)
- Pages: index.html, trainers.html, contact.html
- Reason for any extra page: none added — default scope was already the right fit given 10 trainers with substantial real bios (housed on one Trainers page rather than splitting further).

## Pitch Hook
- Verified observation: The current site's own "Contact" nav item links to `/join`, which renders only a heading, opening hours and address — no email, phone or form. Separately, the site's Instagram icon links to `instagram.com/mwdweddinginspiration`, an unrelated wedding-inspiration account (a leftover template link), not the gym's own account.
- Source URL: https://fredsnw3.com/join ; https://fredsnw3.com (Instagram icon link, confirmed in page's embedded JSON as `"userName":"mwdweddinginspiration"`)

## Allowed Facts
| Fact | Source URL | Used where |
|---|---|---|
| Address: 24 Heath Street, Hampstead, London, NW3 6TE | fredsnw3.com/find-us, /join | Home info strip, Contact, footer (all pages) |
| Opening hours: Monday–Saturday, 6am–9pm | fredsnw3.com/find-us, /join | Home info strip, Contact |
| Email: nebile@me.com | fredsnw3.com (homepage, Nebile Cakir bio) | Home info strip, Contact |
| "Rehabilitation & Personal Training Studio" tagline | fredsnw3.com homepage header | Home hero eyebrow |
| About copy (near Hampstead tube, bespoke 1:1 programmes, choice of skilled trainers) | fredsnw3.com homepage "About Fred's Gym NW3" | Home about section |
| All 10 trainer names, bios, qualifications (Christian Antonee, Benjamin Cooper, Franklyn Morris, Madison Kindall, Maksym "Max" Bojcun, Christopher Chung, Nebile Cakir, Faye Colaço, Glenn Weinstein-Kadir, Damien Belle) | fredsnw3.com homepage bio blocks | Trainers page (full), Home (preview strip of 4) |
| Franklyn Morris quote: "you do not need to be perfect but you do need to be consistent" | fredsnw3.com homepage, Franklyn's bio | Home feature-split section, paraphrased as "a line one of the trainers uses" |
| Christopher Chung quote: "My main goal is to have you feel confident and capable in your body, no matter where you are at in life" | fredsnw3.com homepage, Chris's bio | Trainers page, Chris's card |
| All 11 real photos (studio + 10 trainers) | fredsnw3.com homepage (Squarespace CDN, business's own domain) | Hero, About/feature split, Home preview strip, Trainers grid |

## Do Not Claim
| Claim or uncertainty | Reason |
|---|---|
| Phone number 07734579337 | Found rendered directly next to nebile@me.com inside Nebile Cakir's bio paragraph on the homepage (same personal-bio context as the email). The lead brief supplied to this build explicitly stated "Phone: none" and only asked for the email to be rechecked — a phone number is a new discovery outside this build's authorized fact set, and it is exactly as personal (a named trainer's own mobile, not a general business line) as the already-flagged email. Not used anywhere on the site. Flagging for the top-level session to decide whether to update `LEADS.md` and re-brief. |
| Faye Colaço's personal site www.strengthandflow.com | Appears at the end of Faye's bio on the homepage. This is Faye's own separate personal training business/domain, not Fred's Gym's — linking to it would send demo visitors to an unrelated personal business, so it was left out entirely, consistent with only scraping/linking the business's own site. |
| Exact trainer headcount ("9 uniquely skilled personal trainers") | The site's own intro copy says "9," but 10 distinct named bios with photos are actually rendered on the homepage. Rather than assert either number, the site copy avoids a specific count and just says "the trainers" / lists all 10 found. |
| Instagram account | The only Instagram link found (`instagram.com/mwdweddinginspiration`) is confirmed unrelated (a wedding-inspiration account). Not linked anywhere on the new site, per instructions. |
| Any pricing, class schedule beyond opening hours, or online booking system | Not present anywhere on the source site — not claimed. |

## Asset Manifest
| File | Source URL | Native size | License/credit | Watermark checked | Intended section | Copy match |
|---|---|---|---|---|---|---|
| about_studio.jpg | fredsnw3.com CDN (IMG_8411.jpg) | 2500×1875 | Business's own site | yes — none found | Home hero background | Real studio interior, kettlebell swing, "FRED'S" branded plates visible |
| christian.jpg | fredsnw3.com CDN (272840425_...jpg) | 995×1493 | Business's own site | yes — none found | Home preview strip, Trainers grid | Christian Antonee headshot |
| ben.jpg | fredsnw3.com CDN (ben.jpeg) | 750×977 | Business's own site | yes — none found (only his own "Cooper Coaching" polo branding) | Trainers grid | Benjamin Cooper headshot |
| frank.jpg | fredsnw3.com CDN (frank.jpeg) | 1500×1000 | Business's own site | yes — none found | Home preview strip, feature split, Trainers grid | Franklyn Morris coaching a client |
| madison.jpg | fredsnw3.com CDN (IMG_0357.jpg) | 2500×3333 | Business's own site | yes — none found | Home preview strip, Trainers grid | Madison Kindall on cable machine |
| max.jpg | fredsnw3.com CDN (274550653_...jpg) | 2048×1801 | Business's own site | yes — none found (only his own Adidas top) | Home feature split, Trainers grid | Max Bojcun training with kettlebells |
| chris.jpg | fredsnw3.com CDN (274613772_...jpg) | 349×524 | Business's own site | yes — none found | Trainers grid only (small native size — capped display width) | Christopher Chung headshot |
| nebile.jpg | fredsnw3.com CDN (5604dbd7-...jpg) | 750×500 | Business's own site | yes — none found | Home info context, Trainers grid | Nebile Cakir coaching a client |
| faye.jpg | fredsnw3.com CDN (faye.jpeg) | 576×576 | Business's own site | yes — none found | Trainers grid only | Faye Colaço training alongside a client |
| glenn.jpg | fredsnw3.com CDN (f9dc38a7-...jpg) | 1024×683 | Business's own site | yes — none found | Home preview strip, Trainers grid | Glenn Weinstein-Kadir portrait |
| damien.jpg | fredsnw3.com CDN (273686782_...jpg) | 636×577 | Business's own site | yes — none found | Trainers grid only | Damien Belle headshot |

## Design Notes
- Palette: near-black ink (#121210), warm paper off-white (#f4f1e8), single electric-lime accent (#d7ff3f) — editorial black-and-white photography treated like a fitness magazine, deliberately distinct from the gritty red/gold identity already used for another gym in this pipeline (gav-the-champ-kickboxing-gym).
- Typography: Bebas Neue (condensed display) + Inter (body), loaded via Google Fonts `<link>` (no build step).
- Image layout pattern: wrapper aspect-ratio + `object-fit: cover` throughout (trainer photos have very mixed native aspect ratios — portrait, landscape and square — so a fixed-ratio wrapper keeps the grid aligned). All trainer photos additionally run through `filter: grayscale(1)` to unify tone, since several source photos were already B&W and a couple were greyscale-adjacent color.
- Trainer grid column max-width capped at 20rem specifically so the smallest native photo (Christopher Chung, 349×524) never needs more than a ~1.0x scale-up — see upscale audit below.
- Risk notes: no phone, no working contact form (mailto only — no backend), no Instagram link (source link confirmed wrong/unrelated).

## Builder QA
- Contrast: PASS at all 3 breakpoints on all 3 pages (0 real violations after fixes; see QA_REPORT.md for the one documented script blind-spot, manually verified)
- Upscale mobile: PASS, 0 violations, 0 broken
- Upscale tablet: PASS, 0 violations, 0 broken
- Upscale desktop: PASS, 0 violations, 0 broken
- Broken images: none
- Manual checks: see QA_REPORT.md for full detail. Fixed during build: `.pipeline/qa/contrast-audit.js` oklch()-parsing gap (shared-script fix), several `--muted`-on-paper contrast failures, a `.photo-frame img` aspect-ratio sizing bug (HTML width/height attrs overriding CSS aspect-ratio), and two Contact-page color-leak bugs from nesting a dark card inside an `.on-paper` section.
