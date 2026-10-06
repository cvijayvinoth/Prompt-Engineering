# Sequential Prompting (Prompt Chaining)

## Overview
Sequential Prompting (also known as Prompt Chaining) is a technique where you break a large, complex task into a series of smaller, sequential steps. Instead of asking a Large Language Model (LLM) to do everything in one massive prompt, you feed the **output** of Prompt 1 directly into Prompt 2 as its **input**, and so on.

By narrowing the model's focus at each step, you drastically reduce the chance of the LLM "forgetting" constraints, dropping formatting rules, or hallucinating information. 

## When to Use It
- **Multi-stage Workflows:** E.g., Drafting an article -> Editing for tone -> Formatting to HTML.
- **Data Transformation:** Extracting data from unstructured text, then categorizing it.
- **Context Window Management:** When the desired output is too long or complex to be reliably generated in a single response.

## The Pipeline

1. **Prompt 1 (Generation):** Create the core content (e.g., our 7-Day Meal Plan).
2. **Prompt 2 (Extraction):** Pull specific data from the output of Prompt 1.
3. **Prompt 3 (Formatting):** Reorganize the extracted data for a specific use case.

---

## Example: From Meal Plan to Supermarket List

In this scenario, we already have our generated 7-day South Indian vegetarian meal plan. Now, we want to create a highly organized grocery list. If we asked the LLM to do both the meal plan AND the categorized list in the very first prompt, it would likely fail or miss ingredients. Instead, we chain them.

### Step 1: Generate the Meal Plan
*(We use the `meal_plan_prompt.md` from the root directory to generate the 7-day table. We save this output as `[MEAL_PLAN_OUTPUT]`)*

### Step 2: Extract the Ingredients

```text
# ROLE
Act as a meticulous culinary assistant.

# TASK
Review the provided 7-day South Indian vegetarian meal plan and extract every single ingredient required to cook all the meals listed.

# INSTRUCTION
- Read the [MEAL_PLAN_OUTPUT] carefully.
- Deduplicate items (e.g., if "Moong Dal" is used on Day 1 and Day 4, only list it once).
- Do not list pantry staples like water or basic salt.
- Output ONLY a raw, comma-separated list of ingredients. Do not add bullet points or categories yet.

# INPUT
[Insert MEAL_PLAN_OUTPUT here]

```

## Expected Output 2
Idli rice, urad dal, toor dal, moong dal, fenugreek seeds, drumstick, snake gourd, carrots, curry leaves, mustard seeds, grated coconut, ragi flour, yogurt, ...

### Step 3: Categorize for the Supermarket
# ROLE
Act as an efficiency expert organizing a shopping trip.

# TASK
Take the provided raw list of ingredients and organize them into standard supermarket aisles to make shopping as fast as possible.

# INSTRUCTION
Sort the ingredients into the following exact categories:
1. Fresh Produce (Vegetables & Fruits)
2. Dairy
3. Dry Goods & Lentils (Dals, Rice, Millets)
4. Spices & Condiments

Format the output as a Markdown checklist with the categories as H3 headers.

# INPUT
[Insert Output 2 here]

## Expected Output 3 (Final Result):
### Fresh Produce
- [ ] Drumstick
- [ ] Snake gourd
- [ ] Carrots
- [ ] Curry leaves
- [ ] Grated coconut

### Dairy
- [ ] Yogurt

### Dry Goods & Lentils
- [ ] Idli rice
- [ ] Urad dal
- [ ] Toor dal
- [ ] Moong dal
- [ ] Ragi flour

### Spices & Condiments
- [ ] Fenugreek seeds
- [ ] Mustard seeds
