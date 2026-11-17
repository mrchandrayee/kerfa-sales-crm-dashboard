# Kerfa — Sales & Operations Dashboard

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-blue?style=for-the-badge&logo=github)](https://mrchandrayee.github.io/kerfa-sales-crm-dashboard/)
[![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org) [![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org) [![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](./LICENSE)

A runnable responsive HTML/CSS/JavaScript reconstruction of the newly uploaded 5.33-second screen recording (720 × 1280, 30 fps).

## Run locally
1. Extract `kerfa-sales-crm-dashboard.zip`.
2. Open `index.html` in Chrome, Edge, Firefox or Safari.
3. No npm install or build step is required.

Optional local server:
```bash
python3 -m http.server 8000
```
Then open `http://localhost:8000`.

## What the recording shows

The application branding reads **Kerfa** (the small sub-brand text under the logo is partly legible as “Home & ...”). The interface is a warm charcoal / dark olive sales dashboard with peach accent buttons and blurred interior-photo background.

Top navigation:
- Overview
- Pipeline
- Orders
- Quotes
- Accounts
- Products
- Team
- Reports

### Overview screen
- Greeting: “Good morning, Amara”
- Quarter note: Q4 is 28% through; team booked $115,329 of a $395k target.
- Booked revenue: **$431,106**, +20% vs last year.
- Revenue chart compares this year and last year across 13 weeks.
- Quarter pace: **29.2% of $395k**, ahead by $6.1k.
- Next up: Walnut sample review, Studio Olkafor Interiors, 11:30 AM.
- Pipeline snapshot and recent activity.

### Pipeline screen
- 24 open deals worth **$227,942**, weighted **$104,766**.
- Kanban stages: New lead, Showroom visit, Quote out, Negotiating, Won.
- Team member filters and deal search.
- Example cards visible include Home office ($2,700), Dining set for six ($2,700), Primary bedroom ($10,940), Holiday stool order ($7,164), Autumn stools ($2,940).

### Accounts screen
- 21 accounts across four channels; 21 with an open deal.
- Channel summary cards: Trade & designers ($528k), Hospitality ($291k), Retail partners ($232k), Direct & showroom ($270k).
- Account cards with company, location, lifetime revenue, category and open-deal count.
- Examples: Saltmarsh Inn, Inés Duarte Studio, Northwall Design Co., Harbor Lane Suites, Arbor & Vale.

### Team screen
- Six people; $115,329 booked of a $395k quarter.
- Q4 leaderboard with attainment, booked revenue and pipeline.

## Visible source code extracted from the video

The bottom code-preview panel is labelled `src/motion.ts`. Its readable first 11 lines show a TypeScript helper called `slidePill`. The screen is small and the rest of the function is clipped in the visible preview; the readable portion is transcribed here:

```ts
export function slidePill(pill: HTMLElement, target: HTMLElement) {
  const to = edges(target);              // its l / r / t / b inset in the bar
  const st = pill.__st ?? { ...to };
  const vertical = Math.abs(to.t - st.t) > Math.abs(to.l - st.l);
  const fwd = vertical ? to.t > st.t : to.l > st.l;
  // the leading edge goes first and faster; the trailing edge catches
  // up, so the pill stretches like a drop instead of sliding stiffly
  const [lead, trail] = vertical
    ? (fwd ? ['b', 't'] : ['t', 'b'])
    : (fwd ? ['r', 'l'] : ['l', 'r']);
  const paint = () => gsap.set(pill, { clipPath: clip(st) });
  // Further GSAP tween calls continue below the visible crop.
}
```

The full animation helper is not entirely visible in this recording. The `edges()` and `clip()` helpers, and the remaining tween configuration, are not shown clearly enough to claim an exact full extraction. This project implements navigation styling separately in CSS/JavaScript; GSAP is not required.

## Implemented features
- Responsive Overview, Pipeline, Orders, Quotes, Accounts, Products, Team and Reports screens.
- Revenue chart, quarter progress and upcoming activity cards.
- Kanban deal board with stage movement via clicking a deal card.
- Pipeline search and team filter controls.
- Accounts category filters and text search.
- New deal modal with name, account, value and stage; newly added deal appears in Pipeline.
- Theme toggle and notifications demo.

## Project files
- `index.html` — application shell
- `styles.css` — responsive dashboard design
- `app.js` — demo data, screen rendering and interactions
- `README.md` — extraction notes and run instructions

## Accuracy and limitations
This is a screen-based reconstruction, not the original Kerfa source repository. The code panel shows only a small portion of `src/motion.ts`; only legible lines are transcribed above. The rest of the app is recreated from visible screens. Some small labels and data are approximate. Deal records, orders, quotes, accounts, team figures and charts are local demonstration data. There is no connected CRM backend, database, authentication, email, payment, inventory, or live reporting service. New deal actions are stored in browser memory only and reset on refresh.

## 👨‍💻 Author

**mrchandrayee** · [GitHub](https://github.com/mrchandrayee)

## 📄 License

[MIT License](./LICENSE)
