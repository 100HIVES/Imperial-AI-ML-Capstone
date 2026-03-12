# MODEL_CARD.md

# Model Card for the BBO Optimisation Approach

## 1. Overview

**Model / approach name:**  
Adaptive Human-in-the-Loop Black-Box Optimisation Workflow

**Type:**  
Sequential optimisation workflow for bounded continuous black-box functions

**Version:**  
Repository snapshot prepared after Week 12 submission, with evaluated results through Week 11

## 2. Intended Use

### Suitable use cases
This approach is suitable for:
- small-budget optimisation problems,
- unknown objective functions with expensive evaluations,
- bounded continuous search spaces,
- and educational demonstrations of exploration versus exploitation.

### Use cases to avoid
This approach is not suitable for:
- large-scale optimisation with thousands of evaluations,
- problems requiring guaranteed global optimality,
- safety-critical automation without stronger validation,
- or real-time control systems that need immediate feedback and automatic deployment.

## 3. Approach Details

### High-level strategy
This project did not rely on a single rigid optimisation algorithm throughout. Instead, it used a staged, evidence-driven workflow:

1. **Early rounds:** broad search and signal discovery  
   The first phase focused on learning the rough shape of each function’s behaviour by testing points that could reveal structure.

2. **Middle rounds:** identify repeatable good regions  
   Once some functions started to show stronger areas, the process became more local. Repeatedly good regions were treated as candidate basins worth refining.

3. **Later rounds:** reduce randomness, refine selectively  
   In later weeks, step sizes became smaller for stable high-performing functions, while a limited amount of exploration was retained for unstable or ambiguous functions.

### How the strategy evolved across the first ten rounds
- **Weeks 1–3:** exploration dominated because there was too little information to exploit confidently.
- **Weeks 4–6:** repeated improvements in some regions justified local refinement.
- **Weeks 7–10:** the process became more structured, with function-specific behaviour shaping the next query:
  - stable, high-performing functions were refined conservatively,
  - volatile functions were handled more cautiously,
  - and poor broad exploration was gradually reduced when it stopped adding useful information.

### How decisions were made
The decision process was guided by:
- best-so-far outputs,
- repeated evidence from nearby points,
- sensitivity to step size,
- stability versus volatility of each function,
- and the remaining query budget.

This made the workflow more systematic over time, even though it remained human-guided and reflective rather than fully automated.

## 4. Performance

### Evaluation metric
Because the hidden global optima are unknown, performance was assessed using:
- **best observed output value** for each function,
- **trajectory over time** (whether weekly outputs improved, stagnated, or regressed),
- and **stability of high-performing regions**.

### Best observed outputs through Week 11
- **Function 1:** 0.910133194293295
- **Function 2:** 0.6768844175376618
- **Function 3:** -0.03002872213038304
- **Function 4:** -0.47230185316754314
- **Function 5:** 4373.570415182914
- **Function 6:** -0.4287594021355935
- **Function 7:** 1.7926545796727735
- **Function 8:** 9.8291924183256

### Performance summary
The overall pattern was mixed but informative:
- Functions **1, 2, 5, 7, and 8** showed strong improvement relative to early weeks.
- Function **4** improved dramatically from very poor initial values, even though it remained negative.
- Functions **3 and 6** were harder to improve consistently and appeared more sensitive or less forgiving under the available query budget.

## 5. Assumptions and Limitations

### Core assumptions
This approach assumes that:
- observed outputs contain enough structure to support sequential improvement,
- repeated strong local performance is informative,
- and small local adjustments can be useful once a promising region is found.

### Limitations
- The workflow is based on a **very small number of evaluations**.
- Higher-dimensional functions remain **sparsely sampled**.
- Local success does **not** prove global optimality.
- Some decision steps depend on **human judgement**, which improves flexibility but reduces strict automation.
- Because the hidden functions are external to the repository, this project record is more reproducible as a **documented process** than as a fully rerunnable benchmark.

### Potential failure modes
- premature over-exploitation around a local peak,
- under-exploration in higher dimensions,
- late-stage confirmation bias around earlier strong regions,
- and sensitivity to noisy or misleading single observations.

## 6. Ethical and Transparency Considerations

Transparency matters here because black-box optimisation can easily look stronger on paper than it really is if only final scores are reported. By documenting:
- what data was available,
- what assumptions were made,
- how the strategy changed,
- and where the limitations are,

the repository becomes more reproducible, more honest, and more useful to others.

This is especially important for real-world adaptation. In practical ML and optimisation settings, reproducibility and documentation are often as important as raw performance because other people need to understand:
- where the evidence came from,
- how much trust to place in it,
- and what would need to change before applying the same ideas elsewhere.

## 7. Why this model card is enough for this repository

This model card is intentionally concise but complete enough for the capstone purpose. It explains:
- what the approach is,
- how it was used,
- how it changed over time,
- what performance looked like,
- and what the main constraints are.

More detail could be added later if the repository is expanded into a more formal optimisation benchmark or portfolio case study, but for the current project this structure is sufficient to communicate the method clearly.
