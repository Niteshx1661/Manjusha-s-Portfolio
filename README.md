<div align="center">

# Manjusha Patil | Faculty Portfolio

**An editorial portfolio site for a Computer Science educator with 18+ years in the classroom.**

[![Live](https://img.shields.io/badge/live-manjusha--patil.netlify.app-2f7ba6?style=for-the-badge)](https://manjusha-patil.netlify.app)
![HTML5](https://img.shields.io/badge/HTML5-15243b?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-15243b?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-15243b?style=for-the-badge&logo=javascript&logoColor=b08a3a)
![Netlify](https://img.shields.io/badge/Netlify-15243b?style=for-the-badge&logo=netlify&logoColor=white)

[**View the live site**](https://manjusha-patil.netlify.app) &nbsp;·&nbsp; [**Open the CV**](https://manjusha-patil.netlify.app/Manjusha-Patil-CV.pdf)

<br>

<!--<img src="docs/hero-desktop.png" alt="Desktop view of the portfolio hero: the name set behind a cut-out portrait" width="860">-->

</div>

---

## Overview

| | |
|---|---|
| **Client** | Manjusha Patil, Computer Science faculty at PMCOE Govt. P.G. College, Dhar (M.P.) |
| **Deliverable** | A responsive, single-page portfolio with a downloadable CV and a working contact form |
| **Stack** | Hand-written HTML, CSS and vanilla JavaScript. No framework, no build step |
| **Hosting** | Netlify, deployed continuously from this repository |
| **Role** | Design direction, development, image preparation, deployment |

## The brief

The client has taught undergraduate and postgraduate Computer Science since 2007 and has recently qualified the MPPSC Assistant Professor (Computer Science) 2026 examination. She needed one place that tells her story to three audiences:

- **Students**, who want to see what she teaches and who she is.
- **Peers and institutions**, who need her qualifications and academic service at a glance.
- **Recruiters and selection panels**, who need a clean CV and a reliable way to reach her.

The constraints were just as important as the content. It had to feel like a **college magazine profile, not a developer template**: calm, warm, readable on a phone, and free of the usual dark-mode neon and gradient clichés.

## Design direction

Everything is drawn from the client's own portrait: ivory walls, a sky-blue dupatta, navy ink and a thin line of gold from her jewellery.

| Token | Value | Use |
|---|---|---|
| Ivory | `#f8f3e9` | Page background |
| Navy | `#15243b` | Text, contact section |
| Sky | `#d9e9f3` | Soft bands and glow |
| Blue | `#2f7ba6` | Accents, links |
| Gold | `#b08a3a` | Rare highlights only |

**Typography:** [Fraunces](https://fonts.google.com/specimen/Fraunces) for headings (academic and warm) and [DM Sans](https://fonts.google.com/specimen/DM+Sans) for body text, with system-font fallbacks.

**What was deliberately left out:** particle backgrounds, glass cards, custom cursors, typewriter text, stock hero images and invented statistics. Every number on the site comes from the client's résumé.

## Features

- **Layered 3D hero.** The name sits behind a cut-out portrait, so her head overlaps the letters. The name, a gold ring, the portrait and the side text each move at a different speed on scroll, and the layers shift slightly with the mouse on desktop.
- **Dot field.** 3,000 dots fill in as you scroll, one for each student taught, with 150 turning gold for the projects she has mentored.
- **Career line.** A gold line draws down the page and each milestone lights up as it is reached: M.Sc. 2003, Dhule 2005, Dhar 2007, M.Phil. 2008, NET 2013, MPPSC 2026.
- **Animated impact numbers** that count up once when they scroll into view.
- **Photo gallery** with real photographs from her seminars and classrooms.
- **Working contact form** (Netlify Forms) with honeypot spam protection and inline success and error messages.
- **Downloadable CV** served as a PDF.
- **Light and dark themes** that follow the visitor's device setting.
- **Link previews** for WhatsApp and LinkedIn through Open Graph tags.

## Engineering notes

- **One scroll loop.** The hero writes a single CSS variable (`--y`) from a `requestAnimationFrame` handler, and every layer's `transform` is computed from it in CSS. This keeps the parallax cheap and free of layout thrashing.
- **Portrait cut-out.** The client's photo was background-removed, edge-cleaned and exported as a transparent WebP, then embedded in the page so the hero never shows a broken image. The fade at the bottom is a CSS `mask-image`.
- **Canvas dot field.** Dots are drawn on a `<canvas>` with a seeded random generator, so the fill order is the same on every visit. It scales for high-density screens and redraws when the theme changes.
- **Career line.** Line progress is calculated from the list's position in the viewport, and each milestone switches on when the line passes its dot.
- **Theme-aware CSS.** Colours are CSS custom properties, redefined for dark mode.
- **Contact form.** A static HTML form that Netlify detects at deploy time. Submissions are sent with `fetch`, so the visitor never leaves the page.
- **Print behaviour.** Printing the site itself shows a short note pointing to the official CV PDF, instead of dumping the whole page.

## Privacy by design

The public CV PDF is a web copy of the original résumé with the **home address and phone number removed from the file itself**, not just covered up. Contact is through the form, email and LinkedIn only.

## Accessibility and responsiveness

- Semantic HTML with a clear heading order, descriptive alt text on every photograph, and visible keyboard focus.
- High-contrast navy-on-ivory text and large tap targets.
- Respects `prefers-reduced-motion`: scroll effects, count-ups and entrance animations are switched off, and the final state is shown instead.
- Mobile-first layout that restacks below 1000px: the name moves above the portrait, the text sits below it, and the effects are lighter.
- Tested on desktop and phone-width viewports.

## Project structure

```
.
├── index.html                 # The whole site: markup, styles and scripts
├── Manjusha-Patil-CV.pdf      # Public CV (contact details removed)
├── manjusha-patil.jpg         # Social share image (Open Graph)
├── photo-stage.jpg            # Gallery images
├── photo-teaching.jpg
├── photo-seminar.jpg
├── photo-students.jpg
├── favicon.svg
├── robots.txt
└── docs/                      # README screenshots
```

## Run locally

There is nothing to install. Open `index.html` in a browser, or serve the folder to test it the way a visitor sees it:

```bash
python -m http.server 8000
# then visit http://localhost:8000
```

The contact form only submits on the deployed Netlify site.

## Deployment

1. Push this repository to GitHub.
2. In Netlify, choose **Add new project, then Import from Git**, and select the repository.
3. Leave the build command empty and set the publish directory to the repository root.
4. After the first deploy, open **Forms** in Netlify and add an email notification so messages reach the client.

Every commit to `main` redeploys the site automatically.

## Updating the content

| To change | Edit |
|---|---|
| MPPSC status, for example after the interview | The status chip in the hero, and the dark MPPSC strip under Qualifications |
| Numbers and milestones | The matching section of `index.html` |
| Colours | The CSS variables at the top of the `<style>` block |
| CV | Replace `Manjusha-Patil-CV.pdf` (keep the file name) |
| Photos | Replace the files in the repository, keeping the same names |

## Credits

Photographs and résumé content are the client's own. Fonts are served by Google Fonts under the SIL Open Font License.

## Built by

**Nitesh Patil**, Computer Science Engineering student and full-stack developer.

[GitHub](https://github.com/Niteshx1661) &nbsp;·&nbsp; [LinkedIn](https://www.linkedin.com/in/nitx-patil)

*Need a portfolio or personal site with this level of care? Get in touch.*
