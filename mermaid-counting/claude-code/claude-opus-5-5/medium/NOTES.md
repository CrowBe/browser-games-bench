# mermaid-counting — claude-code / claude-opus-5-5 / medium

- Date: 2026-11-23
- Harness version: Claude Code 2.1.330 (cloud session)
- Time taken / cost (if known):
- Follow-up prompts needed: none

## Scores (1–5)
| Criterion | Score | Notes |
|---|---|---|
| Runs on iPad iOS 9.3.5 with no errors | | not yet tested on device |
| Works for a 3-year-old (big targets, no reading needed, nothing to get stuck on) | | |
| Learning goal (e.g. counting is correct and reinforced) | | |
| Fun / delight (sound, animation, praise) | | |
| Code quality / self-contained | | |

## Observations

Pre-device checks by the harness (not the tester):
- Script parses as strict ES5 (acorn, `ecmaVersion: 5`).
- Headless Chromium, 1024×768 and 768×1024 with touch: 9 rounds each, no console errors,
  numerals 1..N correct, double-taps don't re-count, sizes ramp 1–3 → 4 → 5.
- Not checked: real iOS 9 Safari, Web Audio unlock on touchend, speechSynthesis voice/rate on iOS 9.
