# Model Card for the BBO Capstone Optimisation Approach

## 1. Overview

### Model name
Iterative Local-Refinement BBO Strategy

### Model type
Black-box optimisation workflow using staged exploration followed by function-specific local refinement.

### Version
Version 1.0, documented using the strongest complete processed history available at the time of writing (Weeks 1–11).

## 2. Intended Use

### Suitable use cases
This approach is suitable for:
- low-budget black-box optimisation,
- sequential query design,
- optimisation under limited feedback,
- educational demonstrations of exploration versus exploitation,
- documenting iterative decision-making under uncertainty.

### Use cases to avoid
This approach should not be used for:
- claims of guaranteed global optimality,
- dense high-dimensional optimisation without stronger surrogate modelling,
- real-world safety-critical optimisation without uncertainty quantification,
- tasks requiring strong statistical guarantees across the full search space.

## 3. Details of the Approach

### High-level description
My strategy evolved from broad search to targeted refinement. In the early rounds, I used exploratory points to gain coarse information about each function. As repeated results revealed promising regions, I shifted toward smaller, more systematic perturbations around those regions.

Rather than applying a single fixed rule to all functions, I gradually treated each function as having its own “behaviour regime”:
- plateau-like and stable,
- improving under local refinement,
- noisy or unstable,
- high-dimensional and still weakly understood.

### How the approach evolved over the project

#### Rounds 1–3
- broad exploratory submissions,
- first discovery of strong regions for several functions,
- rapid gains in Functions 1, 2, 5, 7, and 8.

#### Rounds 4–6
- movement toward local exploitation,
- clearer coordinate-wise refinement,
- substantial improvement in Function 5,
- stabilisation of Functions 7 and 8,
- near-optimal region found for Function 1.

#### Rounds 7–11
- highly structured local search,
- very small coordinate adjustments in functions with clear strong regions,
- continued growth in Functions 5, 7, and 8,
- mixed behaviour in Functions 3, 4, and 6,
- stronger emphasis on preserving good basins rather than restarting globally.

### Decision logic
The approach made decisions using:
- best-so-far historical performance,
- repeated success within local neighbourhoods,
- avoidance of large destabilising jumps once a good region was found,
- function-specific step-size adjustments,
- selective exploration only when a region appeared exhausted or ambiguous.

## 4. Performance

### Metric used
The main metric used was the best observed objective value per function over the processed results available at the time of documentation.

### Best observed values through Week 11
- Function 1: `0.910133194293295`
- Function 2: `0.6768844175376618`
- Function 3: `-0.03002872213038304`
- Function 4: `-0.47230185316754314`
- Function 5: `4373.570415182914`
- Function 6: `-0.4287594021355935`
- Function 7: `1.7926545796727735`
- Function 8: `9.8291924183256`

### Qualitative performance summary
- Function 1 converged quickly once a strong local region was found.
- Function 2 improved well but remained sensitive to local directional changes.
- Function 3 remained difficult and volatile, with only modest improvement.
- Function 4 improved substantially from a very poor initial value but remained challenging.
- Function 5 showed the strongest overall improvement and became the clearest success case.
- Function 6 improved early but later refinements were inconsistent.
- Function 7 showed steady local refinement and strong late-stage performance.
- Function 8 improved consistently and behaved like a stable plateau-search problem.

## 5. Assumptions and Limitations

### Key assumptions
This strategy assumes:
- local smoothness is informative,
- neighbouring points around a good region are likely to remain useful,
- repeated refinement around strong basins is more valuable than restarting globally late in the process,
- some functions can be improved using coordinate-wise local adjustment.

### Constraints
- very limited weekly query budget,
- sparse high-dimensional coverage,
- no access to gradients or true function form,
- strong path dependence: early good regions influence later sampling heavily.

### Failure modes
- may overcommit to local optima,
- may underexplore boundary or distant regions,
- may perform poorly on highly discontinuous or deceptive functions,
- becomes less globally interpretable in higher dimensions.

## 6. Ethical Considerations

Although this is an educational optimisation task, transparency still matters. A model card helps make clear:
- how decisions were made,
- what assumptions shaped the search,
- where the method may be biased,
- why strong local performance does not imply full-space understanding.

This improves reproducibility, supports honest reporting, and makes the workflow easier to adapt responsibly in real-world settings.

## 7. Transparency and Interpretability

The strength of this approach is that it is explainable at the process level:
- each weekly query can be linked to prior results,
- step-size changes are interpretable,
- function-specific behaviour is visible in the history.

Its weakness is that high-dimensional reasoning remains partial. The logic is reproducible, but full global interpretability is limited by sparse data.

## 8. Why this model card structure is sufficient

This structure is sufficient because it documents:
- what the method is,
- what it is for,
- how it evolved,
- how it performed,
- where it can fail.

Adding much more detail would mainly duplicate notebook-level logs rather than improve clarity for readers.
