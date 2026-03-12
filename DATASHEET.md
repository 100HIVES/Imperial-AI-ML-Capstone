# Datasheet for the BBO Capstone Project Dataset

## 1. Motivation

This dataset was created to document my query history and returned function evaluations during the Black-Box Optimisation (BBO) capstone project. Its purpose is to support transparent reporting of how my optimisation strategy evolved over time and to make the search process reproducible and interpretable.

The dataset supports the task of sequential optimisation under uncertainty. More specifically, it records how candidate inputs were chosen each week, what outputs were returned, and how those outcomes informed later decisions.

## 2. Composition

The dataset contains weekly query submissions and corresponding function evaluations for eight black-box functions.

### Contents
- 8 optimisation tasks (Functions 1–8)
- Inputs for each function at each week
- Returned scalar output for each function at each week
- Historical sequence of submissions from Week 1 onward

### Structure
Each weekly record contains:
- `week`
- `function_id`
- `input_vector`
- `output_value`

### Dimensionality
- Function 1: 2 variables
- Function 2: 2 variables
- Function 3: 3 variables
- Function 4: 4 variables
- Function 5: 4 variables
- Function 6: 5 variables
- Function 7: 6 variables
- Function 8: 8 variables

### Size
For the main documented phase of the project, the dataset contains the first eleven rounds of query-response pairs across all eight functions:
- 11 weeks × 8 functions = 88 observations

### Gaps
The dataset is sparse by design because only one query per function was submitted each round. Coverage is much denser in low-dimensional spaces than in high-dimensional ones. Some regions of the search space remain unexplored, especially for Functions 6–8. At the time these files were prepared, later rounds were not yet fully processed in the submission portal.

## 3. Collection Process

The dataset was collected during the weekly BBO capstone submission cycle.

### Query generation process
Queries were generated using an iterative optimisation strategy rather than random sampling alone. The process began with broad exploration and gradually shifted toward local refinement around promising regions.

The main patterns in query generation were:
- early exploration to identify promising basins,
- later exploitation through small coordinate-wise adjustments,
- function-specific refinement based on observed trends,
- repeated use of strong-performing neighbourhoods,
- cautious handling of unstable or noisy functions.

### Time frame
The dataset was collected over multiple weekly rounds during Stage 2 of the capstone project.

## 4. Preprocessing and Uses

### Preprocessing
The raw inputs were already bounded in the unit interval and recorded to six decimal places. Minimal preprocessing was applied for documentation purposes:
- consistent formatting of vectors,
- tabulation of week-by-week results,
- organisation into markdown and CSV structures for reproducibility.

In analysis, I sometimes treated the dataset qualitatively through:
- local trend inspection,
- coordinate-wise comparison,
- cluster-like grouping of strong regions,
- comparison of best-so-far outputs.

### Intended uses
This dataset is intended for:
- documenting the optimisation trajectory,
- analysing exploration versus exploitation,
- reflecting on search-space coverage,
- supporting a model card and project retrospective,
- demonstrating transparency and reproducibility in a portfolio context.

### Inappropriate uses
This dataset should not be used as:
- a benchmark for supervised learning model accuracy,
- a representative dataset for general regression tasks,
- evidence of global optimality across the full search space,
- a basis for claims about causality or feature importance beyond this project.

## 5. Distribution and Maintenance

### Availability
This dataset is available through my public GitHub repository for the BBO capstone project.

### Terms of use
The dataset is shared for educational, documentation, and portfolio purposes. It reflects coursework completed within the capstone structure and should be interpreted in that context.

### Maintenance
The dataset is maintained by me as the project author. Updates may include:
- additional weeks,
- cleaned formatting,
- linked notebooks,
- README improvements,
- supporting documentation such as model cards and reflections.

## 6. Assumptions and Limitations

A major assumption behind this dataset is that repeated local sampling around strong regions is informative for optimisation. This improves local refinement but introduces sampling bias toward promising regions and away from underexplored areas.

Another limitation is dimensionality: the same number of weekly samples gives much poorer global coverage in 6D–8D spaces than in 2D–4D spaces.

## 7. Summary

This dataset is a transparent record of an iterative black-box optimisation process. Its main value lies not in scale, but in documenting decisions, trends, uncertainty, and the evolution of a constrained search strategy over time.
