# Tallyhouse — notes for AI coding agents

One HTML file: markup, inline CSS and inline scripts; GSAP with ScrollTrigger, Lenis smooth scroll, all from jsDelivr. No build step, no framework.

## Files
Work from the files: a page read through a link comes back as a summary, and a page rebuilt from it would differ.
```bash
curl -LO https://raw.githubusercontent.com/8bsite/accountant-website-template/main/index.html
curl -LO https://raw.githubusercontent.com/8bsite/accountant-website-template/main/AGENTS.md
curl -LO https://raw.githubusercontent.com/8bsite/accountant-website-template/main/LICENSE
curl -LO https://raw.githubusercontent.com/8bsite/accountant-website-template/main/CREDITS.md
```
In Windows PowerShell type `curl.exe`. Publish `index.html` with LICENSE and CREDITS.md; this file, README.md and `previews/` are not part of the site.

## Do not break
- Keep it one file unless the user asks otherwise; no framework or bundler for copy, colour or photo changes.
- Keep the ids and the `data-8b-section` / `data-8b-motion` attributes. Each section has its styles in `<style data-8b-part="section:<id>">` and its animation, if any, in `<script data-8b-part="scene:<id>">`.
- The scripts find these classes and attributes; when you change a section's markup, keep them or update the script:
  - `section-script:nav`: `.nav__menu` `.menu` `.menu__close`
  - `section-script:opening`: `.op-stage`
  - `section-script:month`: `.mo-bar`
  - `section-script:fees`: `.fe-plan` `.fe-price`
  - `section-script:contact`: `.ct-form` `.ct-status`
  - `scene:opening-cover`: `.op-stage` `.op-ground` `.op-cover` `.op-year` `.op-tile` `.op-statement` `.m-mark`
  - `scene:month-walk`: `.mo-sheet` `.mo-part` `.mo-note` `.mo-key` `.mo-bar__fill`
  - `scene:services-clarity`: `.sv-slabs` `.sv-slab` `.sv-dots` `.sv-photo` `.m-photo__img`
  - `scene:year-filed`: `.yr-pin` `.yr-view` `.yr-track` `.yr-chip` `.yr-chip__fill`
  - `scene:people-settle`: `.pp-grid` `.pp-person`
  - `scene:fees-rise`: `.fe-plan` `.fe-plans` `.fe-fill` `.fe-top`
  - `scene:footer-close`: `.ft-mark` `.ft-year`
- Colours, fonts, radii and shadows are CSS variables in the `:root` block (`data-8b-part="tokens"`); change them there and keep body text at 4.5:1 contrast or more.
- Animations run only when the visitor allows motion (`prefers-reduced-motion: no-preference`); the page must stay readable without them.
- A display line with `style="--len:N"` is sized to fill its width: N is its number of characters, spaces included (`Tallyhouse` → 10).
- Keep the header comment and `<meta name="generator">`. Keep the "Design: 8B" footer link unless the site owner asks to remove it.

## Replace before publishing
- Everything marked `data-8b-placeholder` (og-image, favicon, phone, email, form); remove the attribute once the real value is in. With no real value: no preview image — delete the `og:image` tag and set `twitter:card` to `summary`; no phone, email or address — remove that link or row.
- Book a free call buttons in the nav, the phone menu and the first screen: link to #contact now; point them to your booking page (Calendly, Cal.com) or keep them on the contact form.
- Start as a sole trader / Start as a company / Start with your team in fees: link to #contact now; point them to your sign-up or onboarding URL for each plan.
- Start the switch in switching: link to #contact now; point them to your onboarding form or booking page.
- **The form sends nothing.** `section-script:contact` checks the fields and shows a thank-you message without sending. Pick one:
  - Formspree: set `action="https://formspree.io/f/<id>"` on the form; in the script, before the thank-you message, `await fetch(form.action, { method: 'POST', body: new FormData(form), headers: { Accept: 'application/json' } })` and show it only if the response is ok.
  - Netlify Forms (site on Netlify): add `name="contact" data-netlify="true"` and `<input type="hidden" name="form-name" value="contact">`; send with `fetch('/', { method: 'POST', headers: { 'Content-Type': 'application/x-www-form-urlencoded' }, body: new URLSearchParams(new FormData(form)) })`.
  - No form service: remove the `<form>` together with the script that handles it (it would fail without the form) and keep the email link.
- Invented demo facts (ask the user for the real ones; do not make up prices, dates or addresses):
  - Fees: Sole trader £45, Limited company £125, Company with staff £210 a month, prices exclude VAT, payroll £6 per employee a month, payroll for up to ten in the top plan (fees, both in the text and in each <data value>).
  - Terms: fixed fee, never billed by the hour, extra work quoted first, one month's notice and no exit fee (opening, questions), callback "within one working day" with a fixed price (contact text and the form's status message).
  - Service promises and dates: the one-page report on the 10th of every month, reconciliation by the 8th, payroll approved on the 23rd and paid on the 25th, teams of one to forty, returns filed a week early, first page "usually within two weeks" after switching (opening, monthly-report, services, switching, tax-year, client-stories, accountants).
  - The sample report: Ferris & Daughter Bakery Ltd, September 2026, prepared by Hana Okafor on 10 October; money in £38,420, out £31,960, profit £6,460, up £1,180; cash £14,205 and twelve monthly balances from £7,350 to £15,760 (text and <data value>); Corporation Tax £1,230, VAT £2,940, £4,170 to the tax pot by the 15th; VAT return 31 Oct, payroll for 6 on 25 Oct, quarterly chat 14 Nov 9:30 (monthly-report).
  - Tax rules and deadlines: the 24 dates of the April 2026 to March 2027 calendar (tax-year), Making Tax Digital quarterly updates for sole traders over £50,000 from April 2026 (questions, services, fees). They follow UK rules as of 2026; check them against HMRC every year, and replace them entirely for another country.
  - Software named: Xero, FreeAgent, QuickBooks (questions).
  - Client stories, names and quotes: Mo Adeyemi, The Cutting Room, Easton, barbershop with four chairs, client since 2021, payroll for three; Tom Ferris, Ferris & Daughter, Bedminster, bakery and two market stalls, £4,200 of unclaimed expenses, client since 2023, payroll for six; Priya Nair, Sol Coffee, Stokes Croft, café with nine staff, client since 2024 (client-stories). Use only real clients with their permission.
  - Team: Hana Okafor (founder), Daniel Price, Sofia Marin, Karim Haddad; "all four are chartered" (accountants) and "Chartered accountants for small businesses and sole traders" (footer). "Chartered" is a regulated title: use it only if it is true.
  - Place and hours: "3 Tally Wharf, Bristol BS1 0XX" (contact, footer), "Our office is on Tally Wharf by the harbour" (questions), Bristol and "Bristol's small businesses" (title, meta description, opening), Monday to Friday 8:30 to 17:30 (contact), "© 2026 Tallyhouse Accountants Ltd, Bristol" (footer).
  - The tax-year label "26/27" (navigation, opening, footer) and the statement "one page on the 10th of every month" (opening).
- `<title>`, the meta description and the og tags; photos (Unsplash, see CREDITS.md) when the user has their own.

## Notes
- The bar chart in the sample report and the fee blocks read their numbers from <data value="…"> elements: when you change a figure, change the value too and the heights follow.
- The colour tint and the dot screen on the photos are CSS over ordinary photos, so a new photo takes the slab colours on its own; the three slab colours are --color-3, --color-4 and --color-5 in :root.
- Without JavaScript the report bars and the fee blocks have a uniform height (the figures stay in the text), and the phone menu button cannot open the overlay; the sections stay reachable from the first screen and the footer.
- The tax-year track is pinned for about 2.7 screens of scroll on desktop and about 4 on phones, so that each of the twelve months gets its moment; cut months or chips to shorten it.

## Common edits
- Rebrand: search the old name (`Tallyhouse`) in any letter case and replace every match; change the favicon letter and colours in `<link rel="icon">`.
- Photos: replace `src` and delete `srcset` and `sizes` (they list Unsplash sizes), keep `width`/`height` to the new photo's ratio, update `alt` and CREDITS.md.
- Remove a section: delete its markup, its `section:<id>` and `scene-style:<id>` styles, its `scene:<id>` and `section-script:<id>` scripts, and links to `#<id>`.
- Native scroll instead of smooth scroll: delete the Lenis block in `page-init` and the Lenis `<script>` tag.

## Check and publish
- Open the page at 375 and 1440 px, with reduced motion on, with the console open.
- Search `data-8b-placeholder` and the old name: nothing should be left but class names.
