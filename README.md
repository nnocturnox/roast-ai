# ROAST.AI — Toxic Art Critic

> *You draw. It judges. Nobody wins.*

![HTML](https://img.shields.io/badge/HTML-single%20file-orange?style=flat-square)
![CSS](https://img.shields.io/badge/CSS-vanilla-blue?style=flat-square)
![JS](https://img.shields.io/badge/JavaScript-vanilla-yellow?style=flat-square)
![No dependencies](https://img.shields.io/badge/dependencies-none-green?style=flat-square)
![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-ready-brightgreen?style=flat-square)

---

## What Is This?

ROAST.AI is a browser-based drawing game where you're given a secret word and 60 seconds to draw it on a canvas. A "highly intelligent" AI watches your every stroke in real time — and absolutely tears you apart for it.

The AI never correctly identifies what you drew. That's not a bug.

**Live demo:** [nnocturnox.github.io/roast-ai](https://nnocturnox.github.io/roast-ai)

---

## How to Play

1. Click **ENTER THE ARENA**
2. A secret word appears at the top (e.g. `CAT`, `PIZZA`, `DRAGON`)
3. Draw it on the canvas using your mouse or finger
4. Watch the AI terminal on the right fill up with... feedback
5. Click **DONE** or wait for the 60-second timer
6. Receive your final verdict
7. Click **SHARE MY SHAME** and send it to your friends

---

## Features

### 🎨 Drawing Canvas
- Freehand drawing with adjustable brush size
- Eraser tool
- Clear button (the AI notices and judges you for it)
- Touch support for mobile and tablet

### 🤖 Toxic AI Personality
- **Live commentary** fires every 5–8 seconds while you draw
- **Context-aware reactions** — the AI responds differently based on:
  - How fast or slow you're drawing
  - How many times you erased
  - Whether you cleared the canvas entirely
  - Whether you drew anything at all
- **Word-specific verdicts** — 20 words each with 4 unique roast lines
- **Wrong guesses** cycling through options like `"a disappointed economist"`, `"abstract regret"`, `"Tuesday, but worse"`
- **Confidence meter** that fluctuates wildly and never exceeds 25%

### 💀 Final Verdict
After you're done drawing, the AI delivers a personalized verdict combining your time, stroke count, erase count, and the specific word. Example outputs:

> *"I've analyzed 47 million cat images. This is not one of them."*

> *"This 'house' violates 14 building codes and 1 law of physics."*

> *"You drew nothing. In 60 seconds you drew absolutely nothing. And somehow that is the most impressive thing I've witnessed all day."*

### 📤 Share Your Shame
One-click sharing via the **Web Share API** (mobile) or clipboard copy (desktop). The share text includes your verdict so people know exactly what happened.

---

## Tech Stack

This is intentionally a **zero-dependency, single HTML file** project.

| Layer | Choice | Reason |
|---|---|---|
| Structure | Vanilla HTML | No build step, instant deploy |
| Styling | Vanilla CSS | CSS variables, animations, no framework needed |
| Logic | Vanilla JavaScript | No React, no Vue, no npm |
| Fonts | Google Fonts (JetBrains Mono) | Loaded via CDN link tag |
| AI | Fake | Cleverly fake |

The "AI" is a deterministic system using stroke count, erase count, time elapsed, and randomized roast pools. No API calls, no backend, no cost, no latency.

---

## Deploy to GitHub Pages

**Step 1** — Create a new repository on GitHub (e.g. `roast-ai`)

**Step 2** — Add the file and rename it to `index.html`:
```bash
mv roast-ai.html index.html
git init
git add index.html README.md
git commit -m "initial commit"
git branch -M main
git remote add origin https://github.com/your-username/roast-ai.git
git push -u origin main
```

**Step 3** — Enable GitHub Pages:
- Go to your repo → **Settings** → **Pages**
- Source: `Deploy from a branch`
- Branch: `main` / `root`
- Click **Save**

**Step 4** — Your site is live at:
```
https://your-username.github.io/roast-ai
```

That's it. No build process. No server. No config files.

---

## Project Structure

```
roast-ai/
├── index.html    ← The entire game (HTML + CSS + JS in one file)
└── README.md     ← You're reading this
```

---

## Customization

Everything lives inside `index.html`. The relevant sections are clearly separated:

**Add new words** — edit the `WORDS` array:
```js
const WORDS = ['cat', 'dog', 'house', ...];
```

**Add word-specific roasts** — extend the `WORD_VERDICTS` object:
```js
const WORD_VERDICTS = {
  yourword: [
    'Roast line one.',
    'Roast line two.',
  ],
};
```

**Add live commentary** — edit the `LIVE_COMMENTARY` array:
```js
const LIVE_COMMENTARY = [
  ['Your comment here.', 'roast'],  // types: roast, info, err, ok, sys
  ...
];
```

**Change the timer** — find `timeLeft = 60` and adjust.

---

## Why "Fake AI"?

Real AI drawing recognition (TensorFlow.js, Teachable Machine, etc.) introduces latency, accuracy problems, and deployment complexity. The fake approach gives you full control over the comedy — you decide exactly how wrong and how brutal the AI is. Users can't tell the difference, and they don't need to.

The point isn't accurate classification. The point is the roast.

---

## Browser Support

Works in any modern browser. Touch events are supported for mobile drawing.

| Chrome | Firefox | Safari | Edge | Mobile |
|--------|---------|--------|------|--------|
| ✅ | ✅ | ✅ | ✅ | ✅ |

---

## License

MIT — do whatever you want with it.

---

<p align="center">
  Developed with <span style="color: #ff0040;">❤️</span> by <a href="https://github.com/nnocturnox">Selin Çoban</a>
</p>
