# RTCFR Prompt Engineering

A practical exploration of structured prompt design using the **RTCFR** framework: **Role → Task → Context → Few Shots → Response**. 

This repository focuses on creating prompts that are clear, reusable, predictable, and consistent across different inputs. Moving beyond simple one-shot questions, these techniques treat prompt writing as software design—building robust templates that guide Large Language Models (LLMs) to exact, high-quality outputs.

---

## The RTCFR Framework

The core of this repository revolves around the RTCFR framework, which breaks a prompt down into five distinct modular blocks:

*   **Role:** Who the AI is acting as (e.g., "Expert Clinical Dietitian").
*   **Task:** The specific objective (e.g., "Create a 7-day meal plan").
*   **Context:** Background information, guardrails, constraints, and editable user variables.
*   **Few Shots:** (Optional but recommended) Examples of inputs and desired outputs to calibrate the AI.
*   **Response:** Strict formatting instructions for the output (e.g., Markdown table, JSON, specific columns).

### Primary Use Case: Reusable Meal Plan Prompt
**File:** `meal_plan_prompt.md`

We apply the RTCFR framework to a complex, real-world task: generating a **healthy 7-day vegetarian South Indian meal plan for weight loss**. 

Instead of a vague "give me a diet plan," this prompt separates fixed instructions from an editable context block (user profile: age, allergies, dislikes, prep time). This ensures the AI respects cultural constraints (no quinoa/avocado; using local millets/gourds) and formats the output perfectly every time.

**Principles Demonstrated:**
- Structured prompt design using RTCFR
- Clear role and task definition
- Separation of fixed instructions and editable context
- Explicit constraints and negative constraints (what *not* to do)
- Controlled response formatting
- Reusability across different users

---

## Advanced Prompting Techniques

Beyond the foundational RTCFR structure, this repository includes multiple `.md` files detailing advanced prompt engineering techniques. Each file contains the theory, use cases, and a concrete example.

### 1. Sequential Prompting
**File:** `advanced/sequential_prompting.md`
Breaking down complex tasks into a pipeline where the output of one prompt becomes the input of the next. 
*   *Example:* Prompt 1 (Extract ingredients from a recipe) → Prompt 2 (Generate a grocery list organized by supermarket aisle).

### 2. Chain of Thought (CoT) Prompting
**File:** `advanced/cot_prompting.md`
Forcing the LLM to expose its reasoning process before delivering the final answer by using phrases like "Let's think step by step." This significantly reduces logic and math errors.
*   *Example:* Calculating the total caloric deficit needed over a month based on basal metabolic rate (BMR) and exercise variables.

### 3. Tree of Thought (ToT) Prompting
**File:** `advanced/tot_prompting.md`
Allowing the model to explore multiple different reasoning paths in parallel, evaluate them, and select the best one.
*   *Example:* Generating three different approaches to overcoming a weight-loss plateau, evaluating the pros and cons of each, and recommending the safest option.

### 4. ReAct (Reason + Act) Prompting
**File:** `advanced/react_prompting.md`
Teaching the model to interleave reasoning traces with actions (like searching a database or using a calculator tool) to ground its responses in reality.
*   *Example:* An AI agent that realizes it needs the exact glycemic index of "red rice," writes an action to search for it, and then continues its reasoning based on the result.

### 5. Multi-Agent Prompting
**File:** `advanced/multi_agent_prompting.md`
Simulating a conversation or debate between multiple specialized AI personas to arrive at a superior, well-rounded output.
*   *Example:* A "Nutritionist Agent" creates a meal plan, a "Budget Chef Agent" critiques it for cost and prep time, and a "Moderator Agent" synthesizes a final, optimized plan.

---

## Repository Structure

```text
├── README.md
├── meal_plan_prompt.md           # Core RTCFR example
└── advanced_prompts/
    ├── sequential_prompting.md
    ├── cot_prompting.md
    ├── tot_prompting.md
    ├── react_prompting.md
    └── multi_agent_prompting.md
