## Retrospective on My BBO Capstone Project

### Initial codebase

I started with a lightweight Python workflow built largely from scratch, using simple scientific Python tools rather than a full black-box optimisation framework. I chose this because I wanted the process to stay transparent and easy to change from week to week. In a low-data setting like this one, being able to understand exactly why a query was chosen felt more useful than relying on a more complex library that might be harder to interpret.

My codebase focused on a few core tasks: storing weekly results, comparing historical performance, formatting submissions correctly, and proposing the next query based on observed trends. I kept the setup modular and simple because the project involved repeated weekly decisions rather than a single one-off training run. My GitHub repository is here:

[PASTE YOUR REPOSITORY LINK HERE]

### Code modification: what changed week by week

The main evolution in my code and reasoning was not a complete change in framework, but a steady movement from broad exploration toward structured local refinement.

In the earliest weeks, the code mostly supported broad exploratory submissions. I had very little information, so the goal was simply to spread queries across the space and see where strong regions might exist. These early rounds were important because they quickly revealed that the eight functions behaved very differently.

From Weeks 3 to 6, my process became much more local and function-specific. I noticed that several functions began to show repeated strong performance in narrow neighbourhoods. Function 1 is the clearest example: once the region near approximately `[0.646362, 0.628–0.630]` appeared, later gains mostly came from very small adjustments rather than large moves. Function 5 was another strong case: the outputs increased dramatically when I pushed some coordinates close to the upper boundary, especially the second, third and fourth variables. This led me to adjust the code and my workflow so that I could hold strong coordinates fixed while only nudging the ones that still seemed uncertain.

From Weeks 7 onward, the most important code-level change was that I treated each function as having its own regime. Some looked stable and plateau-like, some were sensitive to direction changes, and some remained noisy or negative. This meant my later decisions were much less “global strategy” and much more “function-specific micro-adjustment.” The most significant impact came from shrinking step sizes and avoiding unnecessary drift away from previously strong regions.

The single biggest lesson from the weekly adjustments was that simple, disciplined local refinement usually helped more than dramatic strategy changes. The strongest improvements came from learning when not to overreact.

### Final result: how the score evolved

Across the project, the clearest success stories were Functions 1, 5, 7 and 8.

Function 1 improved from essentially near-zero values to a best observed value of about `0.910133`. Function 5 showed the largest absolute improvement, rising from `368.66375` in Week 1 to `4373.570415` by Week 11. Function 7 improved steadily across the project, reaching `1.792655`, and Function 8 showed very stable growth to `9.829192`.

Other functions were more difficult. Function 2 was strong but more sensitive to leaving a good region. Functions 3 and 4 improved compared with the start, but remained harder to optimise consistently. Function 6 improved early, but later gains were less stable.

In the final weeks, improvements became smaller and more local. That was expected. By then, the project had shifted from discovery to refinement, so the goal was less about large jumps and more about avoiding regression while squeezing out marginal gains.

If I had more time or a fresh start, I would introduce two things earlier. First, I would build a more formal experiment log from the beginning so that each change in step size, direction, or function-specific rule was easier to compare. Second, I would test a lightweight surrogate-guided method earlier, especially for the higher-dimensional functions, because those were much harder to reason about manually.

### Trade-offs and decisions

The biggest trade-off throughout the project was exploration versus exploitation.

In the beginning, exploration was unavoidable because I had not yet found any reliable structure. Later, exploitation became more justified because some functions began to show repeatable high-performing regions. The challenge was knowing when exploration had become wasteful and when exploitation had become too conservative.

For stable functions such as 5 and 8, exploitation clearly became the better choice. Once a high-performing region was found, large exploratory jumps were more likely to damage performance than improve it. For more sensitive or less understood functions, especially 2, 3, 4 and 6, I had to keep some exploration alive in the form of small boundary tests or cautious directional changes.

Another major trade-off was simplicity versus sophistication. I could have tried more complex modelling earlier, but I chose to keep the workflow simple and interpretable. In a small-data optimisation problem, I found that disciplined decisions, consistent logging, and local reasoning were often more useful than adding complexity too quickly.

### Learning and application

The most important lesson I learned is that optimisation under uncertainty is really a decision-making problem. The challenge is not only to find a better point, but to decide what kind of information is still worth paying for. That lesson applies directly to future ML work, especially in areas where data is expensive, feedback is delayed, or repeated experimentation has a real cost.

A second lesson is that local structure matters more than I first expected. Once a good region appears, careful refinement often beats broad searching. At the same time, higher-dimensional functions reminded me that sparse data can make false confidence dangerous. In future optimisation or hyperparameter-tuning tasks, I would use this same mindset: broad search first, then disciplined local refinement, with explicit awareness of when a strategy is plateauing.

What surprised me most was how strongly some functions rewarded patience and small changes. I expected bigger algorithmic shifts to matter more, but in practice many of the best gains came from very small, deliberate adjustments around already promising regions. I was also struck by how different peers’ strategies could still make sense. Some leaned more exploratory, some more exploitative, and both could work depending on the landscape.

Overall, the BBO capstone taught me that a good optimisation process is not just about accuracy. It is also about transparency, discipline, and knowing how to adapt as evidence accumulates.
