# How to Create Well-Structured Prompts: A Guide Based on Gemini for Google Workspace

This guide provides a step-by-step process for turning a simple request into a well-structured, effective prompt, based on the principles in the "Gemini for Google Workspace Prompting guide 101."

The core methodology is to structure your prompt around four key pillars: **Persona, Task, Context, and Format**.

---

### The Four Pillars of an Effective Prompt

Think of building a prompt as providing a clear and detailed job description to a highly capable assistant. The more specific you are, the better the result will be.

1.  **Persona (Who should the AI be?)**
    Assigning a role or profession to Gemini helps it adopt the correct tone, style, and expertise for the task.
    *   **Prompt:** Start with "You are a..." or "Act as an..."
    *   **Example:** "You are an expert financial analyst..."

2.  **Task (What should the AI do?)**
    This is the most critical part of the prompt. Use a clear, action-oriented verb to state your primary goal.
    *   **Prompt:** Use strong verbs like `Create`, `Summarize`, `Draft`, `Analyze`, `Compare`, or `Brainstorm`.
    *   **Example:** "...draft a summary of the attached financial report."

3.  **Context (What background information is needed?)**
    Provide the necessary details, background, and constraints. This is where you give Gemini the specific information it needs to produce a relevant and accurate response.
    *   **Prompt:** Include details about the audience, goals, and reference any relevant documents using the `@` symbol (e.g., `@My Project Brief Doc`).
    *   **Example:** "The summary is for the executive board, so focus on key performance indicators and risks. Reference the `@Q3 Earnings Call Transcript` for context."

4.  **Format (What should the output look like?)**
    Specify the structure of the response you want to receive. This ensures the output is in a usable format.
    *   **Prompt:** Include instructions like `in a bulleted list`, `as a table with columns for...`, `in a formal email format`, or `limit the summary to three paragraphs`.
    *   **Example:** "Present the summary as a bulleted list, with a concluding paragraph on the overall outlook."

---

### Step-by-Step Example: From Simple Request to Structured Prompt

Here’s how to apply the four pillars to transform a basic request into a comprehensive prompt.

#### 1. Start with Your Core Request

Begin with a simple statement of what you want to accomplish.

> **Simple Request:** "I need to make an agenda for a team offsite."

#### 2. Build the Prompt with the Four Pillars

Now, enhance the core request by adding details for each of the four pillars.

*   **Persona:** "You are an expert event planner and team facilitator."
*   **Task:** "Create a detailed agenda..."
*   **Context:** "...for a two-day offsite for the 15-person marketing team. The goal is to improve team bonding and plan our Q4 strategy. We will be in Austin, TX. Reference our `@Q3 Performance Review` for key topics to discuss."
*   **Format:** "Present the final agenda as a table with columns for Time, Activity, and Objective. Include at least two icebreaker activities."

#### 3. The Final, Well-Structured Prompt

By combining these elements, you create a prompt that is clear, detailed, and much more likely to yield a high-quality result.

> **Well-Structured Prompt:**
>
> "You are an expert event planner and team facilitator. Create a detailed agenda for a two-day offsite for the 15-person marketing team. The goal is to improve team bonding and plan our Q4 strategy. We will be in Austin, TX. Reference our `@Q3 Performance Review` for key topics to discuss. Present the final agenda as a table with columns for Time, Activity, and Objective. Include at least two icebreaker activities."
