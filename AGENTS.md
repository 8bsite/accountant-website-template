# AGENTS.md: accountant website template

Website for a small accountancy practice that does bookkeeping, tax returns and payroll. One file, `index.html`, with inline CSS and scripts (GSAP, ScrollTrigger, Lenis from jsDelivr); no build step, and none is needed for copy, colour or photo edits.

## Files
Edit these files, not a page fetched by URL (that arrives as a summary).
```bash
curl -LO https://raw.githubusercontent.com/8bsite/accountant-website-template/main/index.html
curl -LO https://raw.githubusercontent.com/8bsite/accountant-website-template/main/AGENTS.md
curl -LO https://raw.githubusercontent.com/8bsite/accountant-website-template/main/LICENSE
curl -LO https://raw.githubusercontent.com/8bsite/accountant-website-template/main/CREDITS.md
```
Upload `index.html`, LICENSE and CREDITS.md; not this file, README.md or `previews/`.

## Keep
- Every `id`, `data-8b-section`, `data-8b-motion` and `data-8b-part` (`section:<id>` styles, `scene:<id>` animation).
- Selectors the scripts use:
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
- `style="--len:N"` = characters in that display line, spaces included: `Tallyhouse` is 10.
- The bar chart in the sample report and the fee blocks read their numbers from <data value="…"> elements: when you change a figure, change the value too and the heights follow.
- The colour tint and the dot screen on the photos are CSS over ordinary photos, so a new photo takes the slab colours on its own; the three slab colours are --color-3, --color-4 and --color-5 in :root.
- Colours and fonts are variables in `:root` (`data-8b-part="tokens"`): `--color-1` #ffffff (page background), `--color-2` #0b0b0b (text, cover, tax year, footer), `--color-3` #fe7141 (orange slab, highlights, buttons), `--color-4` #cdabfe (lavender report section, slab), `--color-5` #d1ddd3 (sage questions section, slab), `--color-6` #595959 (secondary text), `--color-7` #a8a8a8 (muted text on black); body text needs 4.5:1 contrast.
- With reduced motion the page must read in full.
- Keep the header comment and `<meta name="generator">`. Keep the "Design: 8B" footer link unless the site owner asks to remove it.

## Replace
- `data-8b-placeholder` (og-image, favicon, phone, email, form): real value in, attribute out; no value, remove the row (no image: drop `og:image`, set `twitter:card` to `summary`).
- Book a free call buttons in the nav, the phone menu and the first screen: now #contact; owner's target: your booking page (Calendly, Cal.com) or keep them on the contact form.
- Start as a sole trader / Start as a company / Start with your team in fees: now #contact; owner's target: your sign-up or onboarding URL for each plan.
- Start the switch in switching: now #contact; owner's target: your onboarding form or booking page.
- The form in `#contact` (fields `name`, `email`, `phone`, `need`, `message`) sends nothing; `section-script:contact` validates it and shows the thank-you text. Formspree: `action="https://formspree.io/f/<id>"` and `fetch` POST `new FormData(form)` first. Netlify: `data-netlify="true"` and a hidden `form-name`. Or delete it and the script.
- The name Tallyhouse (any letter case); the favicon letter and colours in `<link rel="icon">`.
- Photos (19, Unsplash: opening 8, services 3, switching 1, client-stories 3, accountants 4): `src`, no `srcset`/`sizes`, `width`/`height` to the ratio, `alt`, CREDITS.md.
- `<title>`, meta description, og tags.

## Ask the owner for
All demo text, never to be invented:
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

## Known limits
- Without JavaScript the report bars and the fee blocks have a uniform height (the figures stay in the text), and the phone menu button cannot open the overlay; the first screen and the footer still link the month, services, the tax year, fees and contact, but Questions (#faq) is reachable only through the overlay.
- The tax-year track is pinned for about 2.7 screens of scroll on desktop and about 4 on phones, so that each of the twelve months gets its moment; cut months or chips to shorten it.

## Check
375 and 1440 px, reduced motion on, console clean; `data-8b-placeholder` and Tallyhouse left only in class names.
