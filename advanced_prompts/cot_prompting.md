# Chain of Thought (CoT) Prompting

## Overview
Chain of Thought (CoT) prompting is a technique that forces Large Language Models (LLMs) to articulate their intermediate reasoning steps before arriving at a final answer. Instead of jumping directly from a complex prompt to a conclusion, the model is instructed to "think aloud."

By generating a step-by-step breakdown, the model allocates more computational tokens to the problem, which significantly reduces logic errors, math mistakes, and hallucinations in complex scenarios.

## When to Use It
- **Mathematical Calculations:** Figuring out caloric deficits, scaling recipes, or budget planning.
- **Multi-step Logic:** Planning a schedule with dependencies (e.g., cooking times for different dishes).
- **Edge Cases:** Resolving contradictory constraints (e.g., maximizing protein while remaining strictly vegan and staying under a certain calorie limit).

## Two Approaches

1. **Zero-Shot CoT:** Simply appending the phrase *"Let's think step by step"* to the end of your prompt.
2. **Few-Shot CoT:** Providing the model with a demonstration of the step-by-step reasoning you expect before asking it to solve your actual problem.

---

## Example: Calculating Caloric Deficit for Weight Loss

In this scenario, a standard prompt might cause the LLM to guess a timeline or hallucinate the math. A CoT prompt forces it to calculate the exact variables sequentially.

### The Prompt

```text
# ROLE
Act as a sports nutritionist and mathematical planner.

# TASK
Calculate the daily caloric intake required for the client to safely lose 3 kg over the next 6 weeks. 

# CLIENT CONTEXT
- Current Weight: 80 kg
- Basal Metabolic Rate (BMR): 1,600 kcal/day
- Activity: Burns roughly 400 kcal/day through exercise and non-exercise activity thermogenesis (NEAT).
- Note: 1 kg of body fat is approximately 7,700 kcal.

# INSTRUCTION
Do not just provide the final calorie number. Let's think step by step. Show your exact calculations for:
1. Total Daily Energy Expenditure (TDEE)
2. Total caloric deficit required for the goal
3. Daily deficit required over the 6-week timeframe
4. The final recommended daily intake target