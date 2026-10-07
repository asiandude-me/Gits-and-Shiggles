# MegaCalc

A fake enterprise SaaS company that sells you a calculator, plus the calculator.

The marketing site is calm, tasteful and completely straight-faced. It has a
pricing table, customer testimonials, a leadership team and a careers page. Then
you click **Launch app** and it hands you a screaming neon calculator that
computes your answer, blurs it out behind `RESULT LOCKED 🔒`, and asks you to
choose a payment plan. The contrast is the joke.

## Pages

| File | What it is |
|---|---|
| `index.html` | Landing page — hero, features, how-it-works, testimonials |
| `pricing.html` | Three plans, comparison table, FAQ, terms |
| `about.html` | Company story, values, the team, careers |
| `app.html` | The calculator itself |
| `404.html` | "This page is a premium feature." |
| `assets/site.css` | Shared styling for the marketing pages |

No build step, no dependencies, no framework. Static files all the way down.

## Running it locally

```
git clone https://github.com/asiandude-me/Gits-and-Shiggles.git
cd Gits-and-Shiggles
python3 -m http.server 8000
```

Then open `http://localhost:8000/`. You can also just double-click `index.html` —
everything works off relative paths. (`404.html` is the one exception: it uses
absolute `/Gits-and-Shiggles/…` paths, because GitHub Pages serves it for bad
URLs at *any* depth and relative links would break.)

## The pricing

- **Casual Arithmetic** — $499.99/day, billed every 4 hours. Unlocks `+`. Other
  operators sold separately.
- **Mathemagician Pro** — $9,999.99/week plus 14.7% of lifetime gross earnings,
  auto-renewing every 11 seconds.
- **Enterprise** — the price is `$((47,281 × 3.5) ÷ 0.07) + 19.99`. To determine
  it, simply evaluate the expression using a calculator. Calculator sold
  separately.

## Getting out

There is a way out of the paywall, and it is deliberately hostile: a 7-pixel
"no thanks" link that runs away from your cursor three times before giving up,
then three escalating guilt-trip dialogs, then a cancellation progress bar that
fills to 97% and changes its mind. Survivors return to the calculator wearing a
permanent **FREE TIER — ads enabled, answers disabled** banner.

## Heads up: the app page is intentionally loud

Scrolling stripes, wobbling buttons, emoji explosions on every keypress, two
marquees running opposite directions. That's the point. It is loud on purpose
but not hazardous on purpose:

- **Every animation has a period of at least 400ms (under 3Hz)**, and nothing
  strobes the full viewport — below the photosensitive-seizure threshold.
- **`prefers-reduced-motion` gets a real alternative.** All animation stops, the
  background becomes a static gradient, particles are disabled at the source,
  and the fleeing link becomes an ordinary visible button. Every joke survives as
  text; only the motion goes.
- **Sound is muted by default**, behind a button you press on purpose.

## Accessibility

The chaos is decorative. The app underneath is not.

- Real `<button>` elements with `aria-label`s; the display is an `<output>` with
  `aria-live="polite"`.
- Dialogs are `role="dialog" aria-modal="true"`, focus-trapped, `Escape`-dismissible,
  and restore focus on close.
- **The escape hatch only flees from a mouse.** It's reachable on the first `Tab`
  and fires on `Enter`, every time. Keyboard users are never trapped.
- Skip links, one `<h1>` per page, and a real dark mode on the marketing site.
- Text meets WCAG AA (4.5:1) in both light and dark themes — there's an automated
  contrast audit that measures gradient backgrounds, not just flat ones.

## What it doesn't do

There are no inputs, forms, or fields anywhere on any page. The subscribe buttons
are dead ends that tell you your money isn't absurd enough. Nothing is collected,
stored, or transmitted. It's a joke about paywalls, not a paywall.

## The calculator is real

Four functions, decimals, chained operations, a clear key. `1 ÷ 0` gives `NOPE`.
Float dust is rounded off, so `0.1 + 0.2` is `0.3` like you wanted and not like
the IEEE 754 committee wanted.

You just can't read the answers.
