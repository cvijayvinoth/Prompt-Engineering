# Prompt Evaluation & Scoring Checklist

## Overview
A prompt is only as good as its worst output. Because Large Language Models (LLMs) are probabilistic, a prompt that works perfectly on Monday might fail on Tuesday if the instructions aren't rigid enough. 

This file provides a standardized checklist and scoring matrix to evaluate the robustness of your prompts (including RTCFR, CoT, ToT, ReAct, and Multi-Agent templates) before deploying them in production.

## The 5-Point Evaluation Matrix

Score your prompt out of 25 points by running it 3 times with different variable inputs, grading the LLM's output against these five categories (1-5 points each).

### 1. Constraint Adherence (0-5 Points)
*Did the LLM obey both positive and negative constraints?*
- [ ] **5:** Perfect adherence. Did exactly what was asked, strictly avoided what was forbidden (e.g., no avocado or quinoa in the South Indian diet).
- [ ] **3:** Followed main instructions but slipped on minor negative constraints (e.g., included one restricted ingredient).
- [ ] **1:** Ignored major constraints or fundamentally misunderstood the task.

### 2. Format Compliance (0-5 Points)
*Did the LLM output the exact data structure requested?*
- [ ] **5:** Perfect formatting. Output was strictly the requested Markdown table, JSON, or specific column layout without any introductory conversational fluff ("Sure, here is your table:").
- [ ] **3:** Correct core format, but included unwanted conversational text before or after.
- [ ] **1:** Completely broke the format (e.g., returned a bulleted list instead of a table).

### 3. Role & Tone Consistency (0-5 Points)
*Did the LLM maintain the requested persona?*
- [ ] **5:** Deeply internalized the role. Tone, vocabulary, and perspective perfectly matched the persona (e.g., Clinical Dietitian vs. Traditional Chef).
- [ ] **3:** Adopted the role initially but drifted into a generic "AI assistant" voice halfway through.
- [ ] **1:** Ignored the role entirely; sounded like a standard chatbot.

### 4. Robustness to Edge Cases (0-5 Points)
*How did the prompt handle difficult or contradictory variables?*
- [ ] **5:** Handled extreme inputs gracefully (e.g., "Budget is zero," or "Allergic to all lentils") by offering logical alternatives or stating limitations clearly.
- [ ] **3:** Handled standard inputs well but broke down or hallucinated when given a difficult constraint.
- [ ] **1:** Failed completely or generated dangerous/illogical advice when tested with an edge case.

### 5. Reasoning Transparency (0-5 Points) *(For CoT/ToT/ReAct)*
*Is the model's logic clear, mathematically sound, and grounded?*
- [ ] **5:** Step-by-step logic is flawless. Math is correct. In ReAct, it successfully searched and utilized factual data instead of guessing.
- [ ] **3:** Reasoning was mostly good, but skipped a critical step or made a minor arithmetic error.
- [ ] **1:** Logic was circular, math was wildly incorrect, or it hallucinated facts without using provided tools.

---

## Testing Methodology

To properly vet a prompt, put it through this three-phase stress test:

1.  **The Baseline Test:** Run the prompt with standard, expected variables. (Does it work under ideal conditions?)
2.  **The Edge-Case Test:** Run the prompt with conflicting variables (e.g., asking for a high-calorie weight-loss plan, or a dairy-free meal plan that requires paneer). (Does the prompt force the LLM to resolve the conflict logically?)
3.  **The Formatting Stress Test:** Ask for a complex output (like a nested JSON object or a multi-column table) and see if the parser breaks. 

If your prompt scores below 20/25 consistently, you need to revisit the **Context** and **Response** blocks of your RTCFR framework to tighten the guardrails.