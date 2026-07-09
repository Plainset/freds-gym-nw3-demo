# Pipeline Status — Fred's Gym NW3

Operational handoff only. `LEADS.md` and `OUTREACH_LOG.md` remain the source of truth.

- Current phase: Build complete, QA complete, REVIEW complete (independent pass, 2026-07-09), DEPLOY complete (2026-07-09), post-deploy client-feedback FIX complete and redeployed (2026-07-09). Not sent.
- Last trusted commit: see `git log` on `main` — latest fixes the Home "bespoke programmes" blank-space CSS bug and converts trainer qualifications from a click-to-reveal `<details>` to always-visible plain content, per real client feedback from Alex after reviewing the live site. Working tree confirmed clean before redeploy.
- Known untrusted state: none — both client-reported issues root-caused, fixed, and independently rechecked live at desktop (1280px) and mobile (375px); contrast and upscale audits rerun on index.html and trainers.html with zero regressions (see QA_REPORT.md "Post-Deploy Client Fix (2026-07-09)" section).
- Client-feedback fix summary:
  - Blank space below the Home "Bespoke programmes, not a class timetable" heading: root cause was `.intro-grid`'s second column (containing `.chip-row`, an unshrinkable `flex: none` chip list with `overflow-x: auto`) blowing out its grid track width due to the CSS grid-item default `min-width: auto`, squeezing the sibling text column and leaving most of the section blank. Fixed with `.intro-grid > div { min-width: 0; }` in `assets/css/style.css`.
  - Trainer qualifications were hidden behind a `<details><summary>Qualifications</summary>` click-to-expand element on `trainers.html` (all 10 trainer cards). Converted to a plain always-visible `<div class="trainer-quals"><p class="quals-label">Qualifications</p><ul>...</ul></div>` — same verified facts from `BUILD_BRIEF.md`, no interaction required. Also removed the now-dead `:has(details[open])` CSS rule and updated the Trainers page lede copy (no longer says "open each profile for qualifications").
- Next exact action: Draft and send outreach email per AGENTS.md step 7 (top-level session handles drafting/sending this round).
- Deploy URL: https://plainset.github.io/freds-gym-nw3-demo/ (repo: `Plainset/freds-gym-nw3-demo`, branch `main`, Pages source path `/`). Re-verified 2026-07-09 after the client-feedback fix: live URL loads with both fixes present (see commit/push step).
- Outreach state: not started.
- Flags for Alex:
  - A phone number (07734579337) was found on the live source site, rendered directly next to the nebile@me.com email inside Nebile Cakir's personal bio paragraph — same personal-contact context as the email, not a general business line. Not used on the built site (reconfirmed by review: zero matches anywhere in the built HTML/CSS). Worth deciding whether to fold into `LEADS.md`/outreach messaging as an additional caveat-qualified contact route, same as the email.
  - Site has 10 named trainers with full bios/photos, not 9 as the source site's own copy claims — built copy avoids stating an exact headcount rather than asserting either number (reconfirmed by review).
