# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static personal portfolio site for Salan Katuwal, served at www.salankatuwal.com.np (custom domain via `CNAME`, i.e. GitHub Pages). There is no build step, package manager, linter, or test suite — files are served as-is.

To preview locally, serve the repo root with any static server, e.g.:

```
python3 -m http.server 8000
```

Use a server rather than opening files directly: the demo pages reference the favicon with an absolute path (`/assets/img/favicon.png`).

## Structure

- `index.html` — the entire site in one page. Sections are anchored by id (`#hero`, `#about`, `#resume`, `#services`, `#portfolio`, `#contact`) and linked from `#navmenu`; `main.js` scrollspy highlights nav links by matching `href` hashes to section ids, so a new section needs both a matching `<section id>` and a nav link.
  - `#services` is used as the **projects** list (each project has a GitHub link and a "Demo" link).
  - `#portfolio` is used as the **certificates** grid: each card opens a Bootstrap modal (`#certificateModalN`) showing `certificate/certificate_N.png`. Adding a certificate means adding both a card and its matching modal further down in the file.
- `bookstore.html`, `marksheet.html`, `todolist.html` — standalone "Demo" pages, each just a full-screen YouTube iframe of a project walkthrough. New project demos follow the same pattern.
- `assets/js/main.js` — template behavior (header scroll state, mobile nav, preloader, AOS, Typed.js hero text from `data-typed-items`, skill bar animation, GLightbox, Isotope, Swiper, hash-scroll, scrollspy). Features are initialized by querying for classes/data-attributes in the HTML, so they only activate if the markup exists.
- `assets/css/main.css` — site styles on top of Bootstrap.
- `assets/vendor/` — third-party libraries committed as-is (Bootstrap, Bootstrap Icons, AOS, Typed.js, GLightbox, Isotope, Swiper, PureCounter, Waypoints, php-email-form). Don't edit these.

The README lists PHP as a backend, but there is no PHP in the repo; the contact form was removed and the contact section now only shows email/phone/social links.
