# Tree of Thought (ToT) Prompting

## Overview
Tree of Thought (ToT) prompting is an advanced technique that allows Large Language Models to simulate human-like decision-making. Instead of following a single line of reasoning (like Chain of Thought), ToT prompts the model to generate multiple different "branches" of thought, evaluate the merits of each path, and then deliberately select the best one.

This method transforms the LLM from a simple text generator into an analytical problem solver capable of self-correction and comparative evaluation.

## When to Use It
- **Strategic Planning:** When there are multiple viable ways to solve a problem and you need the best one.
- **Complex Troubleshooting:** Diagnosing issues like a weight-loss plateau or resolving schedule conflicts.
- **Creative Constraints:** Designing a meal plan or workout routine where different variables (time, budget, preference) compete.

## The Three Stages of ToT
1. **Brainstorming (Generate Branches):** Ask the model to create 3-4 distinct approaches to the problem.
2. **Evaluation (Assess Branches):** Ask the model to objectively list the pros and cons, or assign a score to each approach based on strict criteria.
3. **Selection (Prune and Conclude):** Ask the model to select the most optimal approach and justify the final decision.

---

## Example: Overcoming a Diet Plateau

In this scenario, a user following the South Indian vegetarian diet has stopped losing weight. We use ToT to explore different interventions rather than just arbitrarily cutting calories.

### The Prompt

```text
# ROLE
Act as a senior clinical dietitian specializing in Indian vegetarian diets.

# TASK
The client has been following a 1,500 kcal South Indian vegetarian meal plan for 8 weeks. They successfully lost 4 kg, but their weight has not changed in the last 14 days (a plateau). Their activity level is unchanged. 

# INSTRUCTION
Use a Tree of Thought framework to determine the best intervention:

Step 1: Brainstorm 3 distinct, actionable strategies to break this plateau without dropping calories below 1,300 kcal. 
Step 2: Evaluate the pros and cons of each strategy specifically for someone eating a South Indian diet (heavy in rice/lentils).
Step 3: Select the absolute best strategy for long-term sustainability and provide a final recommendation.


### The Expected AI Output (Reasoning Trace)

**Step 1: Brainstorming Strategies**
*   **Strategy A (Macro Shift):** Keep calories at 1,500 but shift macros by reducing carbohydrates (rice, idli, dosa) and increasing protein/fat (paneer, sundal, almonds, seeds).
*   **Strategy B (Dietary Break):** Implement a 1-week "diet break" by raising calories to maintenance (approx. 1,800 kcal) to reset metabolism and leptin levels, then return to 1,500 kcal.
*   **Strategy C (Intermittent Fasting):** Keep calories and macros the same, but condense the eating window to 8 hours (e.g., 10 AM to 6 PM) to improve insulin sensitivity.

**Step 2: Evaluating the Strategies**
*   **Strategy A (Macro Shift)**
    *   *Pros:* Highly effective for fat loss; preserves muscle. 
    *   *Cons:* Difficult on a traditional South Indian diet which is inherently carb-heavy. Might cause initial fatigue.
*   **Strategy B (Dietary Break)**
    *   *Pros:* Great for psychological relief; prevents metabolic adaptation. 
    *   *Cons:* Pauses weight loss for a week; client might struggle to return to a deficit afterward.
*   **Strategy C (Intermittent Fasting)**
    *   *Pros:* Easy to implement without changing the actual menu or recipes.
    *   *Cons:* Can lead to overeating during the feeding window; might conflict with social or family dinner times.

**Step 3: Final Selection and Recommendation**
*   *Selection:* **Strategy A (Macro Shift)**
*   *Justification:* While Strategy B and C are valid, the plateau is likely due to metabolic adaptation to the current macro split. Since a South Indian diet can inadvertently lean towards 60-70% carbs, shifting the ratio provides a new metabolic stimulus without starving the client.
*   *Implementation:* Swap morning white rice idlis for whole moong dal (pesarattu) dosas. Replace the evening rice portion with a large bowl of chana sundal and vegetables. Keep total calories at 1,500.