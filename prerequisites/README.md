# Pre-Workshop Prerequisites

**Read [`rl-prerequisites.pdf`](./rl-prerequisites.pdf) before Week 1.**

This is a self-paced primer covering the mathematics and programming the *RL in Production* bootcamp **assumes you already know** — so we never spend lecture time re-teaching basics. Nothing here is new course material; everything maps to something concrete you'll use, most of it in the first week.

## What's inside (14 pages, ~4–6 hours)

| Part | Topic | Needed by |
|---|---|---|
| 1 | Notation fluency — `V(s)`, `max`, `Σ`, `𝔼[·]`, reading recursive equations | **Week 1** |
| 2 | Probability & statistics — expectation, Markov, variance/z-score, sampling, geometric series | **Week 1 (core)** |
| 3 | A little calculus — gradients, chain rule, logs | Week 3 |
| 4 | A little linear algebra — vectors, dot products, "a layer is a matmul" | Week 2 |
| 5 | A little information theory — entropy, KL divergence (the policy "leash") | Week 3 |
| 6 | Programming readiness — Python, NumPy, PyTorch, environment setup | **Week 1 / Week 2** |
| 7 | Systems literacy — GPUs, VRAM, tokens (for the inference half) | Week 4 |
| 8 | Warm-up — what to watch, read, and play first | Anytime |
| 9 | **Self-diagnostic** — 15 questions + answer key + scoring guide | Before Week 1 |

Each topic gives plain-English intuition, the annotated equation, an RL-flavored worked example, and a practice problem with a full solution.

**Do Parts 1, 2, and 6 before the first session.** The rest can wait until the weeks that need them.

## The one idea

Everything in the course is a variation on:

```
V(s) = r + γ · V(s′)
```

The value of where you are = the reward you just got + a discounted look at where you'll be next. If the prerequisites let you read and believe that line, you're ready.

## Building the PDF from source

The PDF is checked in, so you don't need to build it. To regenerate after editing `rl-prerequisites.tex`:

```bash
xelatex rl-prerequisites.tex   # run twice for the table of contents
```

Requires a TeX Live install with XeLaTeX (the document uses `fontspec` + `unicode-math`; fonts: Charter, Avenir Next, Menlo, with TeX Gyre Pagella Math for equations).
