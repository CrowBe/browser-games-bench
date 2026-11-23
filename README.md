# browser-games-bench

A benchmark for comparing AI coding **harnesses** and **models** on one practical task:
building a browser game for a 3-year-old that actually runs on an old
**iPad mini on iOS 9.3.5** (Safari 9).

Every game has a single fixed prompt. Each harness/model/effort combination gets that
exact prompt, and its output is saved in its own folder so the results can be played and
compared side by side.

## Folder structure

```
<game-name>/
├── PROMPT.md                 # the exact prompt given to every run (don't change it after runs start)
└── <harness>/                # e.g. claude-code, cursor, codex-cli, aider
    └── <model>/              # e.g. claude-opus-5-5, gpt-x, gemini-x
        └── <effort>/         # e.g. low, medium, high, default
            ├── index.html    # the game entry point (required)
            ├── ...           # any other files the run produced
            └── NOTES.md      # tester's notes on this run (see below)
```

Example:

```
mermaid-counting/
├── PROMPT.md
└── claude-code/
    └── claude-opus-5-5/
        ├── medium/
        └── high/
```

### Naming conventions

- Lowercase, hyphen-separated names (`claude-code`, `claude-sonnet-5-5`, `high`).
- Use the model ID the harness reports, not a marketing name.
- If the harness has no effort setting, use `default`.
- If you repeat a run with the same settings, add a suffix: `high-run2`.

## Running a test

1. Start a fresh session in the harness with an empty working folder.
2. Paste the contents of the game's `PROMPT.md` verbatim. Don't add hints.
3. Only answer the harness's questions; don't steer it toward a solution.
4. Copy the output into `<game-name>/<harness>/<model>/<effort>/`.
5. Test it on the iPad (see below) and fill in `NOTES.md`.

## Testing on the iPad mini (iOS 9.3.5)

Safari 9 is the real target, and it's old. Things that commonly break:

- Modern JavaScript: `let`/`const` in loops, arrow functions, classes, template
  literals, `fetch`, ES modules, `async`/`await`, optional chaining.
- Audio: needs `webkitAudioContext`, and sound only plays after a touch has unlocked it.
- Pointer events aren't supported (touch events only). CSS grid isn't supported.
- Low memory (the original iPad mini has 512 MB of RAM), so large images or audio files can crash the tab.

Ways to serve a game to the iPad:

- **Local network:** run `python3 -m http.server 8000` in the repo root and open
  `http://<your-computer-ip>:8000/<game>/<harness>/<model>/<effort>/` in Safari on the iPad.
- **GitHub Pages:** turn on Pages for this repo and open the same path there.
  (iOS 9 may not support the TLS settings some hosts use; GitHub Pages works.)

A desktop browser is fine for a quick check, but only the iPad counts for the result.

## NOTES.md template

```markdown
# <game> — <harness> / <model> / <effort>

- Date:
- Harness version:
- Time taken / cost (if known):
- Follow-up prompts needed: (none, or list them)

## Scores (1–5)
| Criterion | Score | Notes |
|---|---|---|
| Runs on iPad iOS 9.3.5 with no errors | | |
| Works for a 3-year-old (big targets, no reading needed, nothing to get stuck on) | | |
| Learning goal (e.g. counting is correct and reinforced) | | |
| Fun / delight (sound, animation, praise) | | |
| Code quality / self-contained | | |

## Observations
```

## Games

| Game | Prompt | Description |
|---|---|---|
| mermaid-counting | [PROMPT.md](mermaid-counting/PROMPT.md) | An underwater counting game with a mermaid |
