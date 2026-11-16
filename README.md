# PrimeLaunch website

Brand website for **PrimeLaunch**, a launch studio by Alfa Team Management (+91 95683 06670).
It tells visitors in one look what we do: we launch new brands end to end.

- Preview: https://alfa-2021.github.io/primelaunch-site/
- Planned home: https://primelaunch.co.in/ (not switched yet, see "Domain" below)

## Files
- `index.html`: the whole site in one file (HTML, CSS and JavaScript). No build step.
- `.nojekyll`: tells GitHub Pages to serve the files as they are.
- `README.md`: this note.

## Sections
1. **Hero** with a 3D launch scene: a faceted gem, orbit rings, satellites and rising sparks. "Plan my launch" scrolls to the planner; "WhatsApp us" opens a chat.
2. **What we launch**: real estate pre-launches, product/D2C brands, restaurants & cafés, clinics, coaching & schools, startups & apps, showrooms. Tapping a card pre-selects it in the planner.
3. **Launch kit**: a 3D cube (it spins by itself; drag to turn it) and the eight services.
4. **30-day launch plan**: a timeline whose progress line fills as you scroll.
5. **Recent work**: three phone mockups drawn in HTML/CSS (no images). Client names are kept private.
6. **Why PrimeLaunch**: five reasons.
7. **Plan your launch**: the visitor picks what, what they need and when. They get a summary card and a "Send my plan on WhatsApp" button with the message typed in. Nothing is stored.
8. **FAQ**, a dark contact band, the footer and a floating WhatsApp button.

## Look and feel
- The default look is **mixed**: dark hero, light content sections, dark plan and contact bands. It stays mixed even when the phone itself is in dark mode.
- The sun/moon button in the header switches to an all-dark look. The choice is remembered on that device (localStorage).
- Colours: trust navy, orange for action buttons, violet for creativity, gold accents, WhatsApp green for chat buttons. Fonts: Sora (headings) and DM Sans (text) from Google Fonts.
- There are no invented numbers, testimonials, client logos or prices on the page.

## 3D and speed
- Three.js r128 loads from cdnjs (exact version, with an SRI hash) after the page is already visible.
- A CSS gem shows first. It stays if the phone can't run WebGL or the CDN is blocked.
- The 3D scene pauses when it is off-screen or the tab is hidden. With "reduce motion" switched on, it shows a still frame.

## How to edit
- **WhatsApp number**: search `index.html` for `919568306670` (wa.me links) and `+919568306670` (call links).
- **Text**: edit it directly in `index.html`. Every section has a comment such as `<!-- 3. Launch kit -->`.
- **Colours**: the tokens are at the top of the `<style>` block (`:root`, `.tone-light`, `.tone-dark`).
- **Planner choices**: the `<form id="planner">` block. If you rename a "What are you launching?" choice, also update the matching `data-pick` on its card in "What we launch".

## Publish
Commit and push to `main`. GitHub Pages redeploys in about a minute.

## Domain (not switched yet)
Today primelaunch.co.in still shows the "Luxury Living in Ganga Nagar" page on Netlify. The suggested switch:
1. Move the Ganga Nagar page to a subdomain on Netlify, for example `ganganagar.primelaunch.co.in`.
2. At GoDaddy, point the apex `@` to GitHub Pages with four A records: 185.199.108.153, 185.199.109.153, 185.199.110.153 and 185.199.111.153. Point `www` with a CNAME to `alfa-2021.github.io`.
3. Once the names resolve, set the custom domain:
   `gh api -X PUT repos/Alfa-2021/primelaunch-site/pages -f cname=primelaunch.co.in`
4. Pull the `CNAME` file that GitHub commits, and keep it.
5. Turn on "Enforce HTTPS" when the certificate is ready.
