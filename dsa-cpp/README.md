# DSA in C++ from Scratch.
This is the repository I've made to track all the stuff I've learnt and applied.

The goal? Just keep going. Get the fundamentals down.

**Calibrated to:** ~23 days home @ 4 hrs/day (~92 hrs) → then 1–2 hrs/day at college
**Starting point:** "mediums with hints" · **Target:** Google intern interviews
**Resource:** [NeetCode 150](https://neetcode.io/practice/practice/neetcode150), already sorted by the [[patterns]] below

---

## The Engine (not optional)

Volume without these rules evaporates. I'll do ~100 problems at home; without spacing I'll *retain* a fraction. These are what make the 92 hours stick.

1. **20-minute cap, then read the full solution.** Honest 20–25 min per new problem. Stuck → read the editorial completely. Not failure — that's the lesson. Past ~25 min stuck, my learning rate is terrible.

2. **Re-solve cold the NEXT day (or 2 days later). ← THE WHOLE GAME, and double-critical when cramming.** Blank file, redo a problem I've seen, no notes. This is the *only* thing converting "I saw it" into "I can produce it under pressure." At this volume, skipping re-solves means most of the cram is wasted motion. Every day below opens with re-solves.

3. **Stay in the pattern cluster.** Same shape back-to-back until I recognize it on sight inside 60 seconds. That recognition *is* interview-readiness.

4. **Talk out loud — ~1 problem/day at home.** Brute-force first → optimize → tradeoffs, narrated. Google weights communication heavily; build the muscle now while I have time.

**Daily structure at home (this matters):**
- **Split the 4 hrs into 2 × ~2 hr sessions** (e.g. morning + evening). Retention beats one 4-hr slog — the back half of a long block is near-useless.
- **Open each session with re-solves** (warm recall), then new problems while fresh. Hardest new problem goes early.
- **Target ~5 new problems/day + 2–3 cold re-solves.**
- **Take ~1 lighter/rest day every 6th day.** Non-negotiable. The schedule below uses ~20 active days; the spare ~3 are my flex/catch-up/rest cushion. I WILL slip a day — that's what the cushion is for, not a failure.

---
## PHASE A — Home Bootcamp (~23 days)

Days follow the real problem-counts: tiny [[patterns]] get 1 day, big ones get 2–3. You clear the first five [[patterns]] in a week, then spend the bulk of the window on the high-value heavy hitters.

| Days | Pattern (count) | Notes |
|------|------------------|-------|
| 1–2 | **Arrays & Hashing (9)** | Foundation. The hashmap→O(n) reflex. |
| 3 | **Two Pointers (5)** | Small + fast. Shrink-from-ends, fast/slow. |
| 4 | **Sliding Window (6)** | The one people re-derive every time. |
| 5 | **Stack (6)** | Include monotonic stack. |
| 6 | **Binary Search (7)** | Include **"binary search on the answer."** → **MILESTONE: 5 core non-tree shapes done, ~33 problems in. Interview-functional.** |
| *flex* | rest / catch-up | |
| 7–8 | **Linked List (11)** | Mechanical. Reversal, cycle detection, merge. |
| 9–11 | **Trees (15)** | Big interview presence. DFS-recursion + BFS-level-order both automatic. |
| 12 | **Heap / Priority Queue (7)** | Top-k / k-th / merge-k. |
| *flex* | rest / catch-up | |
| 13–14 | **Backtracking (10)** | One template: subsets, permutations, combinations. |
| 15 | **Tries (3)** | Quick. Prefix-tree shape. |
| 16–18 | **Graphs (13)** | BFS/DFS grids → topo sort → union-find. **Your graph theory = recognition, move fast.** |
| 19 | **Advanced Graphs (6)** | Dijkstra, MST. Stretch — skip if behind. |
| *flex* | rest / catch-up | |
| 20–23 | **1-D DP (12)** + start **2-D DP (11)** | The big one. RL/DAA front-loads the intuition (state→transition→value). Go slow; this bleeds into college and that's fine. |

**Realistic home outcome:** solid through Graphs, DP underway. That already carries a large share of real interviews.

---

## PHASE B — College Maintenance (1–2 hrs/day)

Goal shifts from *learn [[patterns]]* → *keep them sharp + perform under pressure*. Don't let the cram rot.

- **Finish Dynamic Programming:** 1-D depth → then **2-D DP** (the hard tail — knapsack, LCS, edit-distance, grid DP). my RL/DAA background front-loads the intuition; DP is state→transition→value, which I already think in.
- **Mop up the lower-priority [[patterns]]:** Greedy, Intervals (often pattern-obvious by now), then Math/Bit Manipulation if time.
- **Rotate cold re-solves** of bootcamp [[patterns]] on a loop — this is what stops 92 hours of cram from evaporating once I're busy. ~2–3 re-solves/day, cycling through old [[patterns]].
- **Start mock-interview mode:** ~1 full problem/week solved **timed + talking out loud the entire time**, ideally with a peer or a recording. This is the Google-specific gate the grind alone won't prepare me for.

---

## Milestones

- **~Day 11 (home):** functional on the 5 core non-tree shapes — survivable in a real interview.
- **End of home window:** solid across ~10 [[patterns]]; the bulk of mediums are in reach.
- **A few weeks into college:** DP depth + mock fluency = genuinely interview-ready.

## The one meta-rule
**The schedule serves I, not the reverse.** A pattern clicks fast (math-covered)? Bank the hours, move on. One fights I? Spend the extra day. And honor the rest days — 23 days of grind only works if I don't fry myself by day 10.