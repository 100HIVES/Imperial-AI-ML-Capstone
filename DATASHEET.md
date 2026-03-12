# DATASHEET.md

# Datasheet for the BBO Capstone Query Dataset

## 1. Motivation

### Why was this dataset created?
This dataset was created to document the weekly query history and observed function evaluations from the Black-Box Optimisation (BBO) capstone project. The purpose of collecting it was to support transparent reporting of how the optimisation process evolved over time, including which inputs were tested, what outputs were observed, and how those observations informed later decisions.

### What task does it support?
It supports:
- analysis of black-box optimisation under tight query budgets,
- reflection on exploration versus exploitation,
- documentation of optimisation decisions,
- and educational discussion of sequential decision-making with limited feedback.

## 2. Composition

### What does the dataset contain?
The repository dataset contains the weekly submission history for eight black-box functions:
- Function 1: 2 input variables
- Function 2: 2 input variables
- Function 3: 3 input variables
- Function 4: 4 input variables
- Function 5: 4 input variables
- Function 6: 5 input variables
- Function 7: 6 input variables
- Function 8: 8 input variables

Each evaluated row includes:
- the week number,
- the function index,
- the dimensionality,
- the submitted input vector,
- the observed scalar output,
- and the evaluation status.

### What is the size of the dataset?
At the time these materials were prepared:
- `query_history_weeks_1_11.csv` contains **88 evaluated rows**  
  (11 weeks × 8 functions)
- `submission_status.csv` records submission status through **Week 12**

### What is the file format?
The data is stored as CSV files:
- `data/query_history_weeks_1_11.csv`
- `data/submission_status.csv`

### Are there any gaps?
Yes.
- Week 12 had been submitted, but its output was not yet available when this repository snapshot was prepared.
- The repository documents the weekly query history supplied in my own records; it does not include the full original course seed datasets used by the portal unless added later.
- Coverage is sparse in the higher-dimensional functions, which is an intrinsic limitation of the task rather than a data-entry issue.

## 3. Collection Process

### How were the queries generated?
Queries were generated iteratively, one per function per week, using a practical optimisation workflow that evolved over time:
- early rounds emphasised broad probing and discovery,
- later rounds focused more on local refinement around stronger regions,
- and function-specific adjustments were made when behaviour appeared noisy, flat, or unstable.

The process was human-in-the-loop: previous outputs influenced the next week’s submitted inputs.

### Over what time frame was the dataset collected?
The submission status currently documented spans:
- **26 January 2026** to **11 March 2026**

### What assumptions shaped collection?
The main working assumptions were:
- nearby points may sometimes contain useful information about local structure,
- repeated strong outputs indicate promising regions worth refining,
- and late-stage queries should usually become more selective rather than fully random.

## 4. Preprocessing and Uses

### What preprocessing was applied?
The repository preserves the submitted inputs and observed outputs in raw form.
- Input variables were already constrained to `[0, 1]`
- Outputs were kept in their observed numerical scale
- Blank columns in the CSV are used only where a function has fewer than 8 dimensions

Any temporary analytical transformations used during reasoning (for example, plotting, local comparisons, or ranking by best-so-far performance) were not written back into the stored dataset.

### Intended uses
This dataset is intended for:
- documenting the BBO capstone process,
- educational review of sequential optimisation,
- lightweight analysis of optimisation trajectories,
- and comparison of decision patterns across functions.

### Inappropriate uses
This dataset should **not** be used for:
- claiming a global optimum for any hidden function,
- training high-capacity predictive models as if it were a large benchmark,
- or drawing broad conclusions about black-box optimisation performance outside this limited course setting.

## 5. Distribution and Maintenance

### Where is the dataset available?
It is intended to be stored in the project’s public GitHub repository as part of the final capstone submission.

### What are the terms of use?
This dataset is provided for:
- academic,
- educational,
- and portfolio/documentation purposes.

Because the underlying challenge was course-based, reuse should stay within fair educational and reflective contexts unless the author later expands the repository with additional licensing terms.

### Who maintains it?
The dataset is maintained by the project author.

### Will it be updated?
It may be updated if:
- the Week 12 output becomes available,
- the final query history is appended,
- or the repository is cleaned and extended after submission.
