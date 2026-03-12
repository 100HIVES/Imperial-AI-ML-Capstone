# BBO Capstone Project

This repository contains my Black-Box Optimisation (BBO) capstone project work, including weekly query history, optimisation notes, supporting documentation, and reflection materials.

## Project overview

The goal of this project was to improve the outputs of eight unknown black-box functions using a very limited weekly query budget. Because only one query per function could be submitted in each round, the optimisation process had to balance broad exploration early on with careful local refinement later.

My overall approach evolved from broad probing of the search space toward structured, function-specific local search. As more results accumulated, I focused increasingly on repeated high-performing regions and used smaller coordinate-wise adjustments to improve performance while avoiding unnecessary regression.

## Repository contents

- [`DATASHEET.md`](./DATASHEET.md) — datasheet for the BBO query-history dataset
- [`MODEL_CARD.md`](./MODEL_CARD.md) — model card for my optimisation approach
- [`data/query_history_weeks_1_11.csv`](./data/query_history_weeks_1_11.csv) — structured record of weekly inputs and outputs through Week 11
- [`discussion_posts/21_2_reply.txt`](./discussion_posts/21_2_reply.txt) — paste-ready discussion reply for component 21.2
- [`discussion_posts/25_1_retrospective.md`](./discussion_posts/25_1_retrospective.md) — paste-ready retrospective for component 25.1
- [`discussion_posts/25_3_reply.txt`](./discussion_posts/25_3_reply.txt) — paste-ready discussion reply for component 25.3

## Non-technical summary

This project explored how to improve unknown functions using a very limited number of weekly trials. I began by testing broad regions of the search space, then gradually refined my strategy by focusing on areas that repeatedly gave strong results. Over time, the process shifted from exploration to careful local improvement. The project demonstrates how optimisation under uncertainty depends not only on algorithms, but also on clear decision-making, documentation, and learning from feedback.

## Notes on scope

The documentation in this repository is based on the processed weekly results available to me when I prepared these materials. At the time of writing, the strongest complete result history available covered Weeks 1–11, with later workflow items still pending in the submission portal.

## Reproducibility and transparency

This repository is designed to make the optimisation process easier to follow and audit. The datasheet explains the dataset itself, and the model card explains the logic, assumptions, intended use, and limitations of the optimisation approach.

## Suggested next steps

To fully finalise the repository, I would:
1. add any later-week processed results once available,
2. upload notebooks or scripts used to generate proposals,
3. keep the README updated so that technical and non-technical readers can both follow the project.
