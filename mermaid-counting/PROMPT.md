# mermaid-counting — Test Prompt

Paste everything below the line into the harness exactly as written.

---

Build a browser game called **Mermaid Counting** for my 3-year-old to play on an iPad.

## The game

A friendly mermaid lives under the sea and needs help counting things. Each round:

1. The mermaid asks the child (out loud, by voice) to count objects in the scene, e.g.
   "Can you tap all the starfish?" Things to count could be starfish, shells, fish, or bubbles.
2. Between 1 and 5 objects appear, spread out across the screen.
3. Each time the child taps an object, it reacts (a wiggle, sparkle or bounce), a sound plays,
   and the number is said out loud ("one!", "two!", "three!"). A big numeral also appears
   on or near the object. Each object can only be counted once.
4. When everything has been tapped, the mermaid celebrates and says the total
   ("Three starfish! Well done!"), then a new round starts on its own after a short pause.
5. Start with small numbers (1–3) and slowly include 4 and 5 as the child completes rounds.

## Who it's for

- A 3-year-old who **can't read**. All instructions and feedback must be spoken and shown
  with pictures, not text. Numerals are fine and encouraged.
- There are **no wrong answers and no failure states**: no timers, no lives, no "game over",
  no buzzer sounds. Tapping the background or an object that's already counted should do
  nothing, or something gentle and harmless.
- Tap targets must be big (at least about 80×80 px) and spaced apart so small fingers hit them.
- Nothing that leads out of the game: no links, ads, or menus a toddler could get lost in.
  Ignore stray multi-finger taps, and stop accidental scrolling, zooming, text selection and
  the long-press callout.
- Bright, cheerful, gentle look and sound. Nothing scary or flashing.
- A large, obvious "play" button on first load (this is also needed to unlock audio on iOS).

## Technical requirements (very important)

The game must run on an **original iPad mini running iOS 9.3.5 (Safari 9)**, which can't be updated.

- Use only JavaScript that Safari 9 supports: **ES5**. No `let`/`const`, arrow functions,
  classes, template literals, default parameters, destructuring, spread, `async`/`await`,
  `fetch`, ES modules, or optional chaining. No build step or transpiler. Write ES5 directly.
- No CSS grid, no CSS custom properties (variables), and use `-webkit-` prefixes where Safari 9 needs them.
- Use touch events (`touchstart`/`touchend`); Safari 9 doesn't support pointer events.
  Mouse click support for desktop testing is welcome too.
- Audio: use `window.AudioContext || window.webkitAudioContext` and unlock it during the
  first tap. Sound effects can be generated with the Web Audio API. Use `speechSynthesis`
  for speaking, but the game must still work if no voice is available.
- Must work **fully offline** with **no external dependencies**: no CDNs, web fonts or
  network requests. Draw graphics with inline SVG, canvas, CSS or emoji-free shapes.
  (Emoji may render differently or be missing on iOS 9, so don't rely on them.)
- Keep it lightweight: the device has 512 MB of RAM and a slow CPU. Animations should be smooth.
- Fill the screen in both landscape and portrait (1024×768), and include the right viewport
  meta tag plus `apple-mobile-web-app-capable` so it can be added to the home screen and run full-screen.
- Deliver it as a single self-contained `index.html` file, unless you have a strong reason to use more files.

When you're done, briefly explain how the game works and anything you couldn't verify for iOS 9.
