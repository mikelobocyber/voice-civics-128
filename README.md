# voice-civics-128

Practice the updated 2025 USCIS naturalization civics test (128 questions) by speaking your answers out loud — speech recognition, state-specific answers, no install needed.

Built by [mikelobocyber](https://github.com/mikelobocyber).

![HTML](https://img.shields.io/badge/HTML-single%20file-orange) ![License](https://img.shields.io/badge/license-MIT-green) ![No dependencies](https://img.shields.io/badge/dependencies-none-brightgreen)

---

## What it does

- Covers all **128 official USCIS civics questions** (2025 version)
- **Speech recognition** — speak your answer, the app grades it automatically
- **Fuzzy matching** — small pronunciation differences and slight wording variations still count as correct, matching how the real oral interview works
- **State picker** — select your state to get the correct answers for the four state-specific questions (governor, senators, capital, representative)
- **Three quiz modes** — shuffled, in order (1–128), or the 20 starred questions for the 65/20 senior accommodation
- **Score tracking** — live correct/wrong/skipped counters and a progress bar
- **End-of-quiz summary** — shows your percentage and whether you would pass
- **Works on phones** — responsive layout, large tap targets, tested on iOS and Android

---

## How to use it

**Option 1 — Download and open locally**

1. Download `civics-quiz.html`
2. Open it in Chrome or Edge (right-click the file → Open With → Chrome)
3. Allow microphone access when prompted
4. Select your state, pick a quiz mode, and start practicing

No server needed. The file runs entirely in your browser.

**Option 2 — Host on GitHub Pages**

1. Fork this repository
2. Go to Settings → Pages
3. Set the source to your main branch, root folder
4. GitHub will give you a public URL like `https://yourusername.github.io/civics-quiz`

Anyone can then open that link on any device — phone, tablet, or desktop.

---

## Why you should speak your answers out loud

This is probably the most important thing to know before you start studying: **the civics test is completely oral**. There is no written test, no multiple choice, no typing. A USCIS officer sits across from you, asks a question, and waits for you to answer in English, out loud, in the room.

That changes how you need to prepare.

Reading the answers on a flashcard feels productive, and it is a fine starting point — but recognizing an answer when you see it is a completely different skill from pulling it out of your memory and saying it under pressure. A lot of people know the material cold when they're studying alone at home and then go blank the moment someone is watching and waiting. The only way to avoid that is to practice the way the test actually works: spoken, out loud, one question at a time.

A few specific reasons this matters:

**Some of the answers are harder to say than they look.** Words like "Emancipation Proclamation," "Electoral College," "E Pluribus Unum," and "pursuit of Happiness" are easy to read and easy to stumble over when you're nervous. If you've said them a hundred times before the interview, they come out smoothly. If you're saying them for the first time in the interview room, they might not.

**Silence feels longer than it is.** The officer asks the question and waits. That pause — even a short one — can feel enormous if you're not used to it. People who have only studied silently tend to rush or trail off when they actually have to speak. Practicing out loud trains you to take a breath and answer at a calm, clear pace.

**The interview is not a hostile environment, but it is formal.** An officer is watching you and writing things down. That alone is enough to rattle someone who has never practiced being heard. Speaking your answers out loud, even to an app, even alone in your kitchen, builds the habit of producing answers when someone is paying attention.

The goal isn't to memorize sentences word for word. It's to get to a point where the answers come naturally — where you don't have to think hard, you just know it. That only happens through repetition, and repetition has to be spoken, not silent.

---

## Browser support

| Browser | Speech recognition |
|---|---|
| Chrome (desktop) | ✅ Full support |
| Edge (desktop) | ✅ Full support |
| Chrome (Android) | ✅ Full support |
| Safari (iOS 14.5+) | ✅ Full support |
| Safari (macOS) | ⚠️ Partial |
| Firefox | ❌ Not supported |

Use Chrome or Edge for the best experience. Firefox doesn't support the Web Speech API, so the mic won't work at all — and since spoken practice is the whole point, Firefox isn't a useful option for this app.

---

## Project structure

```
civics-quiz.html    — the entire application (HTML + CSS + JS, one file)
README.md           — this file
```

Everything is in a single HTML file intentionally. There is no build process, no npm, no framework. You can inspect, modify, or redistribute it as-is.

---

## How the answer checking works

The real USCIS civics interview is oral and conducted by a human officer who uses reasonable judgment. This app tries to match that with a three-pass fuzzy matching system:

1. **Exact match** after normalizing (lowercase, strip punctuation)
2. **Substring match** — if what you said contains the correct answer or vice versa
3. **Word-level fuzzy match** — if ≥80% of the answer's words appear in what you said, with up to 1 character of typo tolerance per word (Levenshtein distance)
4. **Short-answer edit distance** — for answers of 3 words or fewer, allows up to 2 character edits overall

This means saying "Jefferson" correctly grades Q78 even if the full answer is "Thomas Jefferson." It also means a mispronounced word like "Jeffurson" will still pass.

---

## State-specific questions

Four questions have answers that vary by state. When you select your state from the dropdown, these are automatically updated:

| Question | What changes |
|---|---|
| Q23 — Who is one of your state's U.S. senators now? | Both senators' names loaded for your state |
| Q29 — Name your U.S. representative. | Representative name, or district note for multi-district states |
| Q61 — Who is the governor of your state now? | Governor's name for your state |
| Q62 — What is the capital of your state? | Your state capital |

> **Important:** Officeholder names change. Always verify current names at [uscis.gov/citizenship/testupdates](https://www.uscis.gov/citizenship/testupdates) before your actual interview. The answers in this app were last verified in May 2026.

---

## The 65/20 accommodation

If you are **65 years old or older** and have been a lawful permanent resident for **20 or more years**, USCIS allows you to study only the 20 questions marked with a star (★). Select **"65/20 special (20 starred only)"** from the quiz mode dropdown to practice only those questions. You must answer 6 out of 10 correctly (60%) to pass under this accommodation.

---

## Contributing

Pull requests are welcome. A few things that would be useful:

- **Corrections** — if an officeholder name is out of date, open an issue or PR with the correct name and a source link
- **Translations** — the 65/20 accommodation allows the test to be taken in the applicant's language; a Spanish version of the questions would be valuable
- **Accessibility** — improvements to screen reader support or keyboard navigation
- **iOS Safari fixes** — speech recognition behavior on Safari can be inconsistent; reproducible bug reports are helpful

Please include a source link when updating any officeholder name (Wikipedia, official government site, or news source).

---

## Data sources

- Questions and answers: [USCIS 2025 Civics Test — 128 Questions and Answers](https://www.uscis.gov/sites/default/files/document/questions-and-answers/2025-Civics-Test-128-Questions-and-Answers.pdf)
- Current officeholders verified via Wikipedia and official government sites, May 2026
- Live updates: [uscis.gov/citizenship/testupdates](https://www.uscis.gov/citizenship/testupdates)

---

## License

MIT — free to use, modify, and distribute. If you improve it, consider opening a pull request so others benefit too.

---

## Disclaimer

This is an independent study tool and is not affiliated with or endorsed by USCIS or the U.S. government. Always use official USCIS materials as your primary study resource. Verify all current officeholder names at [uscis.gov/citizenship/testupdates](https://www.uscis.gov/citizenship/testupdates) before your interview.
