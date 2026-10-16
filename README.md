# Free HTML accountant website template with GSAP scroll animations — Tallyhouse

**Website for a small accountancy practice that does bookkeeping, tax returns and payroll: a free HTML template in one file, with GSAP scroll animations, no build step, MIT license. Made by [8B](https://8b.com/), the AI website builder.**

[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](LICENSE) ![one HTML file: no build](https://img.shields.io/badge/one%20HTML%20file-no%20build-orange) ![GSAP: ScrollTrigger](https://img.shields.io/badge/GSAP-ScrollTrigger-88ce02)

**[Live demo](https://8bsite.github.io/accountant-website-template/)** · **[Use this template](https://github.com/new?template_name=accountant-website-template&template_owner=8bsite)** · **[Download ZIP](https://github.com/8bsite/accountant-website-template/archive/refs/heads/main.zip)**

<a href="https://8bsite.github.io/accountant-website-template/"><img src="previews/desktop.png" alt="Tallyhouse, a free HTML template: first screen on a desktop" width="76.1%"></a> <a href="https://8bsite.github.io/accountant-website-template/"><img src="previews/phone.png" alt="Tallyhouse, a free HTML template: first screen on a phone" width="21.9%"></a>

<p align="center"><a href="https://8bsite.github.io/accountant-website-template/"><img src="previews/scroll.gif" alt="Tallyhouse, a free HTML template: scrolling through the first sections on a desktop" width="40%"></a><br><sub>Scroll animation</sub></p>

A one-page site for a local accountancy firm that serves sole traders and small businesses, with a sample monthly report, services, a tax-year calendar, client stories, team and fixed fees. Flat orange, lavender and sage blocks, hairlines and huge tight type, like an annual report; as you scroll, a black cover spreads over a collage of tinted photos, a dot screen resolves into each service photo, the tax year slides past a line that ticks off each deadline, and the fee blocks rise to their prices.

Good for: accountant or bookkeeper; tax adviser or payroll bureau; small professional practice with fixed monthly plans; any service business that sends clients a regular report. Free for personal and commercial use (MIT), made by [8B](https://8b.com/).

## Quick start

Pick one:

- **With an AI coding agent** (Claude Code, Codex, Cursor, Windsurf…). Download the files into your project (in Windows PowerShell type `curl.exe`):
  ```bash
  curl -LO https://raw.githubusercontent.com/8bsite/accountant-website-template/main/index.html
  curl -LO https://raw.githubusercontent.com/8bsite/accountant-website-template/main/AGENTS.md
  curl -LO https://raw.githubusercontent.com/8bsite/accountant-website-template/main/LICENSE
  curl -LO https://raw.githubusercontent.com/8bsite/accountant-website-template/main/CREDITS.md
  ```
  Then give your agent this prompt:
  ```text
  Read AGENTS.md, then edit index.html. Use this template as the base for a site for <your practice: what you do (bookkeeping, tax, payroll…), for whom, where, your plans and prices, how to book a call>. Keep the layout, the motion and the single-file format; replace the brand name, copy, the sample report, the deadlines for your country, client stories, team, photos, prices, links and contacts, and recolour it through the CSS variables if needed.
  ```
  Give the agent the downloaded file, not a link: an agent reads a link as a summary and would rebuild a different page.
- **No code.** Download the ZIP, unzip it, replace the contacts and texts in `index.html`, put `index.html` into an empty folder and drag that folder onto [Netlify Drop](https://app.netlify.com/drop). The page is online in a minute.
- **On GitHub.** Click **[Use this template](https://github.com/new?template_name=accountant-website-template&template_owner=8bsite)** to get your own copy, then **Settings → Pages → Deploy from a branch → main**. Your site appears at `https://<you>.github.io/<repo>/`.

## What's on the page

- **Navigation** — top bar: wordmark with the year, section links, Book a free call button; phone menu overlay
- **Accounts, kept plainly.** — first screen: a black cover square with headline and two buttons over a collage of eight tinted photos with captions (demo: the trades of the clients), then a black statement screen
- **Your month, on one page.** — sample one-page report beside four numbered notes (demo: a bakery's September)
- **Three jobs, done every month whether you remember or not.** — three full-width colour slabs, one per service, each with a big name, included list, button and a tinted photo
- **Switching takes one phone call.** — how to switch: a large photo, a heading with a highlight and three numbered steps
- **The tax year, handled before it's due.** — pinned horizontal track of twelve months with colour-coded deadline chips (demo: UK tax year April to March)
- **Three kinds of year, kept.** — three client quotes as split blocks: dark panel with portrait and name, colour panel with the quote
- **Four accountants. You will know one of them well.** — team of four: portraits, names and what each looks after
- **Questions people ask before they switch.** — questions and answers on a sage ground (native &lt;details&gt;)
- **Fixed monthly fees. The height of each block is its price.** — three fixed monthly plans as colour blocks whose heights follow their prices
- **Book a free twenty minutes.** — office, phone, email and hours, plus a booking form in a black panel (placeholders)
- **Footer** — black footer: address and contacts, links, a giant year and a width-filling wordmark, copyright and the Design: 8B credit

## Before you publish

- Replace everything marked `data-8b-placeholder` (social preview image, favicon, phone, email, form) and the invented demo facts — prices, dates, address. [AGENTS.md](AGENTS.md) lists them.
- The contact form does not send anything yet: connect it to a form service (Formspree, Netlify Forms) or remove it; [AGENTS.md](AGENTS.md) shows both.

## Customize

- **Colours and fonts**: CSS variables in the `:root` block at the top of `<head>`.
- **Text**: edit it in place. A big display line with `style="--len:N"` fills its width: set N to its new number of characters.
- **Photos**: replace `src`, delete `srcset` and `sizes` (they list Unsplash sizes) and update the `alt` texts.
- **Animations**: each section's animation is one `<script data-8b-part="scene:<id>">` block at the end of the file. For native scroll, delete the Lenis block in `page-init`.

## For developers

- **Stack.** HTML and CSS (custom properties, cascade layers) with GSAP 3.13.0, ScrollTrigger, Lenis 1.3.27 from jsDelivr. No build step, no framework, no npm. 112 KB.
- **Layout of the file.** `<head>`: CSS variables, shared classes, then one style block per section. Then the markup, one element per section with a one-line comment above it. End of `<body>`: small behaviour scripts, the libraries, smooth scroll (`page-init`), the effects, one animation script per section.
- **Browsers.** Chrome and Edge 111+, Safari 16.2+, Firefox 113+ (it uses color-mix(), cascade layers, small/dynamic viewport units).
- **Accessibility.** Motion runs only when the visitor's system allows it; with "reduce motion" the page is complete and still. FAQ answers use native `<details>` and open without JavaScript. Every photo has alt text.
- **External requests.** fonts.gstatic.com, images.unsplash.com, cdn.jsdelivr.net. No analytics, no cookies. To self-host everything (offline use, or Google Fonts and GDPR in the EU), download those files and change the URLs.
- **Licences of the parts.** GSAP is free, commercial use included, under its own standard licence (not MIT); Lenis is MIT; fonts are SIL OFL; photos are under the Unsplash License. See [CREDITS.md](CREDITS.md).

## FAQ

**Can I use it for a client or a commercial site?** Yes. The code is MIT: use it, change it, sell the site you build with it.

**Do I have to keep the "Design: 8B" link?** No. It is welcome, not required.

**Can I use it in React, Next.js, Astro or Vue?** Yes. Move each section's markup and style block into a component and run its animation script in `useGSAP()` (React) or `onMounted` (Vue); start Lenis once. Or keep it as a separate static landing page next to your app (`example.com` for the landing, `app.example.com` for the app).

**Why doesn't the contact form send?** It is a demo. Connect it to Formspree, Netlify Forms or your backend; AGENTS.md has the steps.

**Where are the photos from?** Unsplash; they load from Unsplash's servers. Replace them with your own when you can.

## More free templates

[More 8B templates on GitHub](https://github.com/8bsite) · [8b.com](https://8b.com/)

## License

The template code is MIT licensed — see [LICENSE](LICENSE). Photos, fonts and libraries keep their own licences — see [CREDITS.md](CREDITS.md).
