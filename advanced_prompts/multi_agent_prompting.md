# Multi-Agent Prompting (Simulated Persona Debate)

## Overview
Multi-Agent Prompting is a technique where you instruct a single Large Language Model to simulate a conversation, debate, or collaborative workflow between multiple distinct AI "personas." 

Instead of asking one generalized AI to balance competing priorities (which often results in a generic, watered-down answer), you assign specific, extreme constraints to different agents. The agents critique each other's work, exposing blind spots and refining the output until a specialized "Moderator" agent synthesizes the final result.

## When to Use It
- **Competing Objectives:** Balancing health vs. taste, budget vs. quality, or speed vs. security.
- **Peer Review & Critique:** Having a "Critic" agent specifically look for flaws in a "Creator" agent's draft.
- **Complex Brainstorming:** Simulating a virtual boardroom to generate diverse perspectives before finalizing a strategy.

---

## Example: Balancing Nutrition, Authenticity, and Budget

In this scenario, we want a South Indian weight-loss meal plan, but we know standard nutrition AI often suggests bland food, while a culinary AI might suggest calorie-dense meals. We simulate three agents to negotiate the perfect balance.

### The Prompt

```text
# ROLE
You are going to simulate a collaborative panel of three experts.

# THE EXPERTS
1. Agent A (The Clinical Dietitian): Strictly focused on calorie deficits, high protein, and portion control for weight loss.
2. Agent B (The Traditional South Indian Chef): Strictly focused on authentic taste, traditional cooking methods, and using local, flavorful spices.
3. Agent C (The Moderator): Balances the feedback from Agent A and Agent B to create a realistic, actionable final meal plan.

# TASK
Design a single, perfect Sunday lunch for a client on a 1,500 kcal/day weight-loss plan who loves traditional Tamil cuisine.

# INSTRUCTION
Simulate the following workflow:
1. Agent A proposes a highly clinical, macro-optimized lunch.
2. Agent B harshly critiques Agent A's meal for lack of authenticity and proposes a tastier, traditional alternative.
3. Agent A critiques Agent B's meal for being too calorie-dense.
4. Agent C synthesizes the debate and outputs the final, compromised Sunday lunch recipe with portion sizes.
```

### The Expected AI Output (Simulated Transcript)
**Agent A (Clinical Dietitian):** 
For a 1,500 kcal weight-loss plan, I propose 50g of boiled quinoa, 150g of steamed spinach with zero oil, and 100g of plain tofu. This ensures a low glycemic load and high protein, keeping the lunch strictly under 350 calories.

**Agent B (Traditional Chef):** 
Absolutely not. Quinoa and plain tofu are completely alien to traditional Tamil cuisine; the client will hate this and quit the diet by Monday. Sunday lunch is special! I propose a traditional Bisi Bele Bath made with short-grain rice and toor dal, tempered generously in pure ghee, served with potato fry (urulai kizhangu varuval) and a deep-fried appalam. 

**Agent A (Clinical Dietitian):** 
Agent B, your meal is easily 800 calories. The ghee and deep-fried appalam will completely destroy the client's caloric deficit for the day, and potatoes offer too little protein for the carb load. We need a compromise.

**Agent C (Moderator - Final Synthesis):** 
Both of you make valid points. We need the clinical efficiency of Agent A and the cultural adherence of Agent B. Here is the synthesized Sunday Lunch plan:

**The Final Sunday Lunch:**
*   **Dish 1: Millet Sambar Sadham (Replacing Bisi Bele Bath):** Use Foxtail millet (thinai) instead of white rice to lower the GI. Double the ratio of toor dal and vegetables (drumstick, pumpkin, carrots) to increase fiber and protein. Limit tempering to exactly 1 teaspoon of ghee per serving for authentic aroma without the massive calorie hit. (Portion: 1.5 katoris/cups)
*   **Dish 2: Roasted Yam (Senai Kizhangu) Fry (Replacing Potato Fry):** Parboil the yam, toss in traditional spices (turmeric, chili powder, fennel), and air-fry or pan-roast with just a light spray of sesame oil instead of deep frying. (Portion: 0.5 katori)
*   **Dish 3: Cucumber & Mint Thayir Pachadi (Raita):** Made with low-fat curd to boost protein and provide a cooling contrast, replacing the deep-fried appalam for crunch. (Portion: 1 katori)

*Moderator Note: This satisfies the traditional palate, feels like a hearty Sunday meal, but stays firmly around 450 calories with excellent macro distribution.*

