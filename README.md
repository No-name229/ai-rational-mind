# AI: The Rational Mind

An interactive single-page educational book on Artificial Intelligence, with an illustrated comic companion, *The Chronicles of Q-Bot*.

**Author:** Raid Zhetpis
**Course:** AI Fundamentals (Introduction to Intelligence Applications), Qairu University
**Assignment:** EndTerm creative project (individual)

---

## 1. Overview

The book turns the lecture material into ten chapters. Each chapter has worked explanations, code listings, "Did You Know?" notes, mini-quizzes and, where it helps, a live interactive demo. A ten-episode comic follows the same arc: Arman and his robot Q-Bot meet each chapter's concept in everyday situations in Kazakhstan.

The project uses only vanilla HTML5, CSS3 and JavaScript. There is no framework, no build step and no external runtime dependency, so it works offline.

The visual language is **Japandi**:

| Token family | Role |
|---|---|
| `--cement-*` | micro-cement greys for surfaces and text |
| `--walnut-*` | deep walnut for accents and structure |
| `--glow` | warm 2700K amber, used for emphasis and highlights |

Typography is Inter for text and JetBrains Mono for code.

## 2. Project structure

```
.
├── index.html            # the whole application: HTML + embedded CSS + embedded JS
├── README.md
└── comic/
    ├── cover.webp        # comic cover
    ├── thumbs/           # ep01.webp … ep10.webp  (episode cards in the comic hub)
    ├── ep01/             # p01.webp … p10.webp    (10 panels)
    └── ep02/ … ep10/     # p01.webp … p08.webp    (8 panels each)
```

All CSS and JavaScript are embedded in `index.html`. The only external files are the comic images, which are loaded lazily (`loading="lazy" decoding="async"`).

## 3. Content

### Lecture chapters (`#ch1` … `#ch10`)

| # | Chapter | Main topics |
|---|---|---|
| 1 | Agents & Environments | rationality, PEAS, environment properties, agent architectures |
| 2 | Search Algorithms | problem formulation, BFS, DFS, UCS, A* |
| 3 | Local Search & Optimization | hill climbing, 2-opt, simulated annealing, genetic algorithms, Kazakhstan case studies |
| 4 | Adversarial Search | minimax, alpha-beta pruning, expectimax |
| 5 | Probability & Bayes Nets | Bayes' rule, conditional probability tables, explaining away |
| 6 | Hidden Markov Models | filtering, smoothing, Viterbi |
| 7 | MDP & Reinforcement Learning | Bellman equation, value and policy iteration, Q-learning |
| 8 | Rational Decisions & Machine Learning | utility, maximum expected utility, logistic regression |
| 9 | Neural Networks | perceptron, XOR, ReLU, backpropagation, F1 score |
| 10 | Kazakhstan AI Legal Framework | Law No. 230-VIII ZRK, the seven principles, risk and autonomy classes, labelling, AI audit |

### Sources & AI Use (`#refs`)

A closing page with the generative-AI disclosure (Claude for text, code and the comic script; Google Flow with Nano Banana Pro for the comic illustrations), a note on how the content was verified, and 18 references: textbooks, original papers and the official text of the Kazakhstan AI law.

### Comic episodes (`#comic-1` … `#comic-10`)

| Ep | Title | Concept |
|---|---|---|
| 1 | Wake Up, Unit-01 | agents, PEAS |
| 2 | The Long Road to Almaty | uninformed and informed search |
| 3 | Rush Hour on the Left Bank | local search |
| 4 | Duel Over the Bayterek | adversarial search |
| 5 | The Alarm That Cried Fire | Bayesian reasoning |
| 6 | The Motor That Whispered | temporal reasoning (HMMs) |
| 7 | The Slippery Warehouse | MDPs and reinforcement learning |
| 8 | The Scholarship That Almost Vanished | decisions and learning |
| 9 | Black Ice | neural networks |
| 10 | The Sixty-Second Test | responsible AI and the legal framework |

Each episode contains WebP panels, HTML speech bubbles (`.cmx-say`), hologram readouts (`.cmx-readout`), data tables (`.cmx-table`), a "Brain Upgrade" banner (`.cmx-upgrade`) and an **AI Lesson** card (`.cmx-lesson`) that ties the story back to the chapter.

## 4. Interactive features

- **Six live demos:** simulated-annealing acceptance probability, Bayes' theorem for a diagnostic test, HMM filtering in the umbrella world, value iteration in a 4 × 3 gridworld, activation functions and their derivatives, and a confusion-matrix calculator.
- **Twenty quiz questions** (green for correct, red for incorrect, with an explanation after each answer). The sidebar shows live quiz progress and the number answered correctly on the first try; visited chapters are remembered in the browser's `localStorage`.
- **"Did You Know?" notes** and syntax-highlighted code listings in every chapter.
- **Book Presentation Card** (`#pcard`): a 16:9 card for screenshots, with a QR-code placeholder.
- **Responsive layout:** the sidebar turns into a sticky top navigation bar on narrow screens.

### Keyboard shortcuts

| Key | In the book | In the comic (`#comic*`) |
|---|---|---|
| `→` | next chapter | next episode (hub → Ep 1 → … → Ep 10) |
| `←` | previous chapter | previous episode |

Each episode also ends with pager buttons: back to the previous episode, **All episodes** (the hub), and on to the next episode.

### Routing

The book is a hash-routed single page: `#home`, `#ch1` … `#ch10`, `#comic`, `#comic-1` … `#comic-10`, `#refs`. Every view has a stable, shareable URL.

## 5. Running locally

**Option A, open the file.** Double-click `index.html`. Everything works offline, including the comic.

**Option B, serve the folder** (recommended if your browser restricts `file://`):

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## 6. Deploying to GitHub Pages

1. Create a repository and place `index.html`, `README.md` and `comic/` at the repository root.
2. Commit and push to `main`.
3. In the repository, open **Settings → Pages**, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
4. After a minute the book is available at `https://<username>.github.io/<repository>/`.

The `index.html` at the root is picked up automatically, and all comic paths are relative, so no configuration is needed. Replace the QR-code placeholder on the Presentation Card with a QR code for that URL.

## 7. Browser support

Current versions of Chrome, Edge, Firefox and Safari. WebP images and CSS custom properties are required.

---

*Created for the AI Fundamentals EndTerm. The content follows the course lectures and the Law of the Republic of Kazakhstan No. 230-VIII ZRK "On Artificial Intelligence" (in force from 18 January 2026).*
