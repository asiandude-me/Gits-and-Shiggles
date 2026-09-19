# MEGA CALC 9000

A calculator that works perfectly, right up until you ask it for the answer.

Press `=` and it does the math, shows you the result blurred out behind
`RESULT LOCKED 🔒`, and invites you to choose between three increasingly
unreasonable subscription tiers. The Enterprise tier's price is an arithmetic
expression you'd need a calculator to evaluate. The calculator is sold separately.

There *is* a way out. It's a 7-pixel "no thanks" link that runs away from your
cursor three times, then gives up and hands you over to a chain of guilt-trip
modals and a cancellation progress bar that fills to 97% and then changes its
mind. Get through all of it and you're returned to your calculator, permanently
branded **FREE TIER — ads enabled, answers disabled**.

## Running it

Open `index.html` in a browser. That's the whole thing — one file, no build
step, no dependencies, no server.

```
git clone https://github.com/asiandude-me/Gits-and-Shiggles.git
cd Gits-and-Shiggles
open index.html          # or xdg-open, or just drag it onto a browser window
```

## Heads up: this page is intentionally loud

Scrolling stripes, wobbling buttons, emoji explosions on every keypress, two
marquees going opposite directions. That's the point.

It is loud on purpose but not hazardous on purpose:

- **Every animation has a period of at least 400ms (under 3Hz)**, and nothing
  strobes the full viewport. That keeps it below the photosensitive-seizure
  threshold.
- **`prefers-reduced-motion` gets a real alternative, not a token one.** If your
  OS has reduced motion enabled, all animation stops, the background becomes a
  static gradient, particles are disabled at the source, and the fleeing escape
  link becomes an ordinary visible button. Every joke survives as text — only the
  motion goes away.
- **Sound is muted by default**, behind a button you have to press on purpose.

## Accessibility

The chaos is decorative; the app underneath is not.

- Real `<button>` elements throughout, with `aria-label`s on the operator keys.
- The display is an `<output>` with `aria-live="polite"`.
- Focus rings stay visible through the noise, and focus is restored when dialogs close.
- Modals are `role="dialog" aria-modal="true"`, focus-trapped, and dismissible with `Escape`.
- **The escape hatch only flees from a mouse.** It's reachable on the first `Tab`
  and activates with `Enter`, every time. Keyboard users are never trapped.

## What it doesn't do

It never asks for payment details. There are no inputs, no forms, and no fields
of any kind anywhere on the page — the subscribe buttons are dead ends that tell
you your money isn't absurd enough and send you back to the plans. Nothing is
collected, stored, or transmitted. It's a joke about paywalls, not a paywall.

## The calculator is real

Four functions, decimals, chained operations, and a clear key. `1 ÷ 0` gives you
`NOPE`. Float dust is rounded off, so `0.1 + 0.2` is `0.3` like you wanted and
not like the IEEE 754 committee wanted.

You just can't read the answers.
