# ReAct (Reason + Act) Prompting

## Overview
ReAct (an amalgamation of **Reasoning** and **Acting**) is an advanced prompt framework designed for LLMs that have access to external tools (like search engines, calculators, or databases). 

Standard LLMs rely solely on their internal, pre-trained knowledge, which can lead to hallucinations when asked for highly specific or up-to-date facts. ReAct solves this by forcing the model into a strict loop:
1. **Thought:** The model reasons about what it needs to know.
2. **Action:** The model uses a tool to fetch the missing information.
3. **Observation:** The model reads the result of the tool.
4. *(Repeat until the problem is solved)*
5. **Final Answer:** The model synthesizes the observations into a grounded response.

## When to Use It
- **Fact-Checking:** When building diet plans that require precise macronutrient data or Glycemic Index (GI) values that the model shouldn't guess.
- **Dynamic Data:** When incorporating real-time information (e.g., current seasonal vegetables in a specific region).
- **Complex Tool Use:** When the AI needs to query a calculator, a custom API, or a specific document database.

---

## Example: Verifying Nutritional Constraints

In this scenario, we want the LLM to recommend a traditional South Indian ingredient for a diabetic weight-loss client, but we strictly forbid it from hallucinating the nutritional data. We give it access to a hypothetical tool called `Search_Nutrition_DB`.

### The Prompt

```text
# ROLE
Act as a precise clinical dietitian. 

# TASK
Recommend a traditional South Indian lentil or legume suitable for a diabetic client aiming for weight loss. The ingredient must have a Glycemic Index (GI) under 40 and protein content higher than 20g per 100g.

# TOOLS AVAILABLE
You have access to the following tool:
- Search_Nutrition_DB[query]: Searches a clinical nutrition database and returns exact macro and GI values.

# INSTRUCTION
Use the ReAct format to solve this:
Thought: Think about what you need to do.
Action: Search_Nutrition_DB[your query]
Observation: (The result of your action)
... (repeat Thought/Action/Observation as needed)
Thought: I now have the verified data to make a recommendation.
Final Answer: Provide your recommendation based strictly on the observations.
```

### The Expected AI Output (Reasoning & Action Trace)
Thought: I need to find a South Indian legume that is high in protein and very low in GI. Horse gram (Kollu) and Green gram (Moong) are traditional choices. I should check the exact stats for Horse gram first.
Action: Search_Nutrition_DB[Horse gram raw 100g]
Observation: Horse Gram (raw, 100g) - Calories: 321 kcal, Protein: 22g, Carbs: 57g, Fiber: 15g, Glycemic Index: 32.

Thought: The observation shows that Horse gram has 22g of protein (which is >20g) and a GI of 32 (which is <40). It perfectly fits the client's strict constraints. I do not need to search further. I can now formulate the final recommendation.
Final Answer: I highly recommend **Horse Gram (Kollu)**. Based on clinical data, raw horse gram contains 22g of protein per 100g and has a very low Glycemic Index of 32. It is a staple in South Indian cuisine (often consumed as Kollu Rasam or Sundal) and perfectly aligns with your diabetic weight-loss goals due to its high fiber and protein content stabilizing blood sugar levels.

### Why This Matters for Prompt Engineering
Without the ReAct framework, an LLM might guess the protein content of horse gram as 15g or 25g, or hallucinate a GI value. By forcing the Thought -> Action -> Observation loop, you ensure the AI's final output is anchored in verifiable data rather than statistical probability.