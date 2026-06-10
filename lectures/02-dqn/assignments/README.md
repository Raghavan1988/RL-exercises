# Lecture 2 — Coding Assignments (Q-learning → DQN)

Two partially-filled Colab notebooks. Read the `# ✅ PROVIDED` cells, then fill every `# 📝 TODO`. Each TODO has hints and a sanity-check assert. Both also include short **written ablations** — change one thing, observe, explain in 2–4 sentences.

## Project 1 — Tabular Q-learning on `Taxi-v3`
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/VizuaraAI/RL-in-Production-Bootcamp-Resources/blob/main/lectures/02-dqn/assignments/Project_1_QLearning_Taxi.ipynb)

CPU only, trains in under a minute. You implement the Bellman update line itself —
`Q[s,a] += α(r + γ·maxQ[s′] − Q[s,a])` — plus ε-greedy and the training loop.
**Pass bar:** greedy evaluation ≥ +7 (optimal ≈ +7.9). Stretch: SARSA vs Q-learning.

## Project 2 — DQN from scratch on `Pong`
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/VizuaraAI/RL-in-Production-Bootcamp-Resources/blob/main/lectures/02-dqn/assignments/Project_2_DQN_Pong.ipynb)

**Requires a T4 GPU** (Runtime → Change runtime type → T4). You implement the three DQN
tricks — the replay buffer, the linear ε schedule, and the TD loss with a **target
network**. Atari preprocessing, the Nature-DQN CNN, Drive checkpointing, and GIF
recording are provided. Graded on a correct implementation and an upward reward trend
past 0 — not on hitting +21.

> Tip: in Colab, **save a copy to your Drive** (File → Save a copy in Drive) before you start, so your work and checkpoints persist across disconnects.
