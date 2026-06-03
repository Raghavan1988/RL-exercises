# Tic-Tac-Toe RL Visualizer

A single-page browser visualizer that runs **DP**, **Monte Carlo**, and **TD(0)** on tic-tac-toe **simultaneously**, side by side, so you can watch all three converge to the same value function through different paths.

This is the **first in a series** of in-browser visualizers for the *RL in Production* course. The template (theme, layout, agent-as-class pattern) is intentionally reusable — future lectures will follow this same skeleton.

## How to open

No build step, no server, no dependencies.

```bash
# Just open index.html in any modern browser
open index.html
```

Or serve it on `localhost`:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

Or deploy the `visualizer/` folder as a static site (GitHub Pages, Vercel, Netlify).

## What you see

The page has three sections.

### 1. Three-column live training panel

Each column runs one algorithm independently:

| Column | Shows |
|---|---|
| **Dynamic Programming** | Sweep count · states updated · max change per sweep · V(empty) chart · three diagnostic boards (empty, X-about-to-win, mid-game) with their current V values |
| **Monte Carlo** | Episode count · states seen · running W/D/L tally · V(empty) chart · last episode's final board |
| **TD(0)** | Episode count · transition count · mean &#124;TD error&#124; · V(empty) chart · last episode's final board |

A scrolling **log** at the bottom of each column shows the most recent updates in plain language.

### 2. Convergence charts

Each algorithm has a small line chart plotting **V(empty board) vs. iterations**. By the end of the run all three converge to roughly **+0.99** (the value of the empty board against a uniformly-random opponent). They reach it at very different rates.

### 3. Play against a trained agent

Once any of the three has trained, you can pick it from the dropdown and play a live game. The right-hand panel shows the agent's evaluation `V` of every legal move — useful for understanding what the agent has actually learned.

## Controls

| Button / control | What it does |
|---|---|
| **▶ Play** | Starts the training loop |
| **⏸ Pause** | Pauses all three agents |
| **⟳ Reset** | Wipes everything and re-initializes |
| **Speed slider** | Episodes-per-tick — left = slow + watchable, right = fast |
| **Opponent dropdown** | Choose which trained agent to face |
| **New game** | Start a fresh game · you play X |
| **Agent plays first** | Switch sides · agent plays X, you play O |

## What you should look for

1. **DP converges first.** Usually in 4 sweeps (< 1 second). It "looks at everything, then stops." The chart hits ≈0.99 almost immediately.

2. **MC converges slowly but monotonically.** Each episode contributes one full-trajectory update; variance is high so the curve wobbles up.

3. **TD converges roughly 10× faster than MC** in number of episodes. The per-move bootstrapping lets information propagate through the state space without waiting for episodes to end.

4. **All three reach the same V*** — that's the whole point. The Bellman recursion has a unique fixed point; the algorithms just take different routes.

## How the code is organized (so you can fork it for a future lecture)

The whole app is **one HTML file** (~1000 lines). Embedded JS structure:

```
TTT          ← environment (state, step, legal moves, terminals)
DPAgent      ← value iteration class
MCAgent      ← first-visit Monte Carlo class
TDAgent      ← TD(0) class
UI           ← rendering helpers + chart class
main IIFE    ← wires controls, tick loop, and the play-against-agent widget
```

To build a visualizer for the next lecture (Q-learning / DQN, PPO, etc.) you can keep the entire scaffold and replace:
- the `TTT` module with your environment
- the three agent classes with your algorithm variants

The chart, log, controls, and play-against-agent widget should work unchanged.

## Theme

Warm cream paper (`#F7F2E8`), Fraunces serif for headings, Inter for body, JetBrains Mono for stats/labels. Same palette as the slide deck.

Earth-tone accents:
- **Forest** (`#3D5A4A`) — DP, "value" things
- **Slate** (`#4A5D7E`) — MC, states / math
- **Red** (`#8B3A3A`) — TD, emphasis, X player
- **Ochre** (`#8E6B2F`) — rewards
- **Plum** (`#6B4E7E`) — discount / time

The CSS variables at the top of `index.html` are the single point of truth — change them once and the whole page rebrands.
