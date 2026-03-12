# BBO Capstone Project Repository

## Non-technical summary

This project explores how to find good solutions when the true rules of the problem are hidden and each test is expensive. Every week, I could submit only one new query for each of eight unknown functions. I used the results from earlier weeks to decide whether to search more broadly or refine areas that were already performing well. Over time, the process became more structured and less guess-based. The repository documents my query history, optimisation reasoning, dataset description, and model card so that another reader can understand what I did and reproduce the workflow.

## Project overview

This repository documents my work on the Black-Box Optimisation (BBO) capstone project.  
The task is to maximise eight hidden functions with continuous inputs in the range `[0, 1]`, under a very small query budget.

### Core objective

The goal is to make good sequential decisions under uncertainty:
- learn from a small number of function evaluations,
- identify promising input regions,
- balance exploration and exploitation,
- and improve the best observed output over time.

## Current repository status

- Evaluated weekly history included here: **Weeks 1–11**
- Submission tracking included here: **Weeks 1–12**
- **Week 12** had been submitted, but its output was still pending when these repository materials were prepared.

## Approach in plain language

My overall process was:

1. Start with broader search to understand the space.
2. Track which regions repeatedly gave better results.
3. Reduce step size and refine around strong regions.
4. Keep limited exploration when a function looked noisy, flat, or unstable.
5. Use past results as evidence rather than treating each week as an isolated guess.

This was a practical, human-in-the-loop black-box optimisation workflow rather than a single fixed algorithm.

## Best observed results through Week 11

| Function | Best observed output | Best week |
|---|---:|---:|
| 1 | 0.910133194293 | 9 |
| 2 | 0.676884417538 | 10 |
| 3 | -0.0300287221304 | 3 |
| 4 | -0.472301853168 | 11 |
| 5 | 4373.57041518 | 11 |
| 6 | -0.428759402136 | 2 |
| 7 | 1.79265457967 | 11 |
| 8 | 9.82919241833 | 11 |

## Repository contents

- `README.md` — project overview and accessible summary
- `DATASHEET.md` — datasheet for the BBO query-history dataset
- `MODEL_CARD.md` — model card for the optimisation approach
- `data/query_history_weeks_1_11.csv` — evaluated query history through Week 11
- `data/submission_status.csv` — submission timeline showing Week 12 as pending
- `notebooks/BBO_Capstone_Summary.ipynb` — lightweight notebook for inspecting the stored history

## Data format

The main dataset stores one row per weekly query per function.

Columns:
- `week`
- `function`
- `dimension`
- `x1 ... x8`
- `y`
- `status`

Blank input columns are left empty for functions with fewer than 8 dimensions.

## Intended audience

This repository is designed to be readable by:
- technical readers who want the raw history and documentation,
- course staff reviewing the project,
- and non-technical readers who want a plain-language explanation of the optimisation process.

## Notes on reproducibility

This repository preserves the observed weekly query history and documents the decision process at a high level.  
Because the original evaluation portal is external and the hidden functions are not available here, the repository is best understood as a transparent project record rather than a fully runnable end-to-end benchmark environment.
