# QA Report — Fred's Gym NW3

Use exact pass/fail evidence. "Looks fine" is not a result.

## Pages Checked
- index.html (Home)
- trainers.html (Trainers / Offer)
- contact.html (Contact)

All three checked at desktop (native, ~1345px), tablet (768px), and mobile (375px) via `.pipeline/qa/contrast-audit.js` and `.pipeline/qa/upscale-audit.js` run live against `localhost:4226` (preview server, `.claude/launch.json` entry `freds-gym-nw3-site`).

**Audit-harness note:** this environment's headless preview tab never fires native `loading="lazy"` image loads or the `IntersectionObserver`-driven `[data-reveal]` scroll-reveal, even after real scrolling. Both audit runs therefore force `img.loading = 'eager'` and add `.is-visible` to all `[data-reveal]` elements immediately before checking, so every element on the page (not just what happened to be above the fold/already loaded) is actually measured. Confirmed this is an audit-tooling quirk, not a site defect — forcing eager load resolves it immediately with zero broken images.

## Audit Results
| Check | Result | Evidence |
|---|---|---|
| Contrast audit | PASS (3/3 pages × 3 breakpoints) | 0 real violations after fixes. Only remaining flagged item is a documented false-positive (see Manual Checks). |
| Upscale mobile (375px) | PASS | index: 6/6 imgs checked, 0 violations. trainers: 10/10, 0 violations. contact: 0 imgs (map is an iframe, no `<img>`). |
| Upscale tablet (768px) | PASS | Same totals as mobile, 0 violations, 0 broken, 0 aspect mismatches. |
| Upscale desktop (~1345px) | PASS | Same totals, 0 violations, 0 broken, 0 aspect mismatches. |
| Broken images | PASS | `brokenImages: []` on every page/breakpoint run. |
| Aspect mismatch advisory | PASS | `aspectMismatches: []` on every run (all trainer/feature images use wrapper `aspect-ratio` + `object-fit: cover`, not `fill`). |

## Manual Checks
| Check | Result | Notes |
|---|---|---|
| Text on photo (Home hero) | PASS (manual) | The hero headline, lede, and "Get in touch" ghost button sit over `about_studio.jpg` via a `linear-gradient(in oklch, ...)` scrim (::after on `.hero-media`) plus `text-shadow` on the headline/lede. The contrast script can't see this — it only walks CSS ancestor backgrounds, and the photo is a sibling `<img>`, not a `background-image` on an ancestor — so it reports these 5 text nodes as "light-on-light" against the page's `--paper` fallback. Verified by direct screenshot at desktop and mobile: headline/lede/buttons are clearly legible white/cream text against the dark gradient over the photo, at all three breakpoints. |
| Gradient/::before backgrounds | PASS (manual) | Same hero scrim as above; verified visually. `.eyebrow::before` dash and `:has()`-driven trainer-grid dimming both inspected directly via computed styles — correct. |
| Image/content match | PASS | Every image is the named trainer's own real bio photo or the studio's own interior shot, sourced from fredsnw3.com's own CDN. See `BUILD_BRIEF.md` asset manifest. No stock/mismatched photos used; Faye's card uses her real bio photo (a training-floor action shot) rather than a posed headshot, consistent with what's on the source site. |
| Fabricated claims | PASS | Every factual claim (address, hours, trainer names/bios/qualifications, quotes) is sourced verbatim or lightly paraphrased from fredsnw3.com; uncertain/rejected claims logged in `BUILD_BRIEF.md` → Do Not Claim (phone number, Faye's personal external site, exact trainer headcount, Instagram). |
| Mobile layout | PASS | Verified at 375×812: single-column hero, working hamburger nav (`aria-expanded` toggles true/false, `.main-nav.open` class applied, confirmed via both click test and computed state), trainer grid reflows to 1 column, contact card and map stack correctly. |

## Blocking Issues
| Issue | Evidence | Required fix |
|---|---|---|
| None outstanding | — | — |

## Advisory Issues
- None outstanding (feature-split image sizing, contact-card color leaks, and muted-label contrast were all found and fixed during this build — see Fixed Verification below — not left as advisory).

## Fixed Verification
| Issue | Fix | Recheck result |
|---|---|---|
| `contrast-audit.js` couldn't parse `oklch(...)` computed-style strings (Chrome serializes `color-mix(in oklch, ...)` this way), so it silently fell through to the wrong ancestor background and reported false violations for the header/nav on every page | Added an `oklchToRgb` conversion + regex branch to the shared `.pipeline/qa/contrast-audit.js` `parseColor()` (benefits every future build using this script, not just this one) | Header/nav false violations gone on recheck; script now correctly resolves the header's dark translucent background |
| `.stat-row span`, `.trainer-body ul`, `.mini-card figcaption small`, `.on-paper .hours-table td:last-child`, `.on-paper .lead` all used `--muted` (#8a887c) on `--paper`, giving only 3.16:1 (fails 4.5:1 for normal text) | Added `--muted-strong` (#666456, 4.68–5.28:1 depending on context) and repointed all of the above to it; `.mini-card figcaption small` also split into an ink-context default (`--muted-on-ink`) vs. an explicit `.on-paper` override | Rechecked on index.html and trainers.html at all 3 breakpoints: 0 violations |
| Dev placeholder text "Open Mon–Sat, tabular hrs" was accidentally left in the live Home page stat row copy | Replaced with the real content: "Mon–Sat" / "6am – 9pm" | Verified in rendered page text |
| `.photo-frame img` (Home "Why one-to-one" feature image) rendered at its raw natural height (1801px, ~4.6× container width) instead of the intended 4:3 ratio — the HTML `width`/`height` attributes create a presentational height hint that wins over `aspect-ratio` unless `height` is also explicitly set in CSS, per the `AGENTS.md` image-sizing note | Added `height: auto;` to `.photo-frame img` | Section height dropped from 2030px to 621px; image now measures 523×392 (4:3, 0.26× of native — far under the 1.3× upscale ceiling) |
| Contact page: `.contact-card`'s `.eyebrow` and `.hours-table td:last-child` inherited color overrides from the *outer* `<section class="on-paper">` ancestor (CSS specificity let the `.on-paper` descendant rules leak into a nested always-dark card), giving 3.15–3.46:1 instead of 4.5:1 | Added `.contact-card`-scoped overrides pinning `--accent` / `--muted-on-ink` regardless of ancestor section class | Rechecked: 0 violations |
| Contact page: `.notice` box set a light `--paper-dim` background but inherited the ambient light `--text-on-ink` color from its dark `.contact-card` parent, giving 1.15:1 (invisible text) | Added explicit `color: var(--text-on-paper)` directly on `.notice` | Rechecked: 0 violations |

## Verdict
PASS
