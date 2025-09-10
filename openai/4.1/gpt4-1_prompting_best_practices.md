# GPT-4.1 Prompting Best Practices Guide

This guide provides a distilled set of best practices for creating effective prompts for the GPT-4.1 model family, based on the official prompting guide.

## 1. Core Principles

- **Be Literal and Specific:** GPT-4.1 follows instructions more literally than previous models. Clearly and unequivocally state your desired behavior. If the model's output is not what you expect, a single, firm sentence is often enough to correct its course.
- **Structure is Key:** A well-organized prompt leads to better results. Use Markdown, XML, or other clear delimiters to structure your prompt logically.
- **Iterate and Evaluate:** AI engineering is an empirical process. Build informative evaluations and iterate on your prompts to find what works best for your specific use case.

## 2. Agentic Workflows

To build effective agentic systems, include three key reminders in your system prompt.

1.  **Persistence:** Ensure the model understands it's in a multi-turn process and should not stop prematurely.
    ```
    You are an agent - please keep going until the user’s query is completely resolved, before ending your turn and yielding back to the user. Only terminate your turn when you are sure that the problem is solved.
    ```
2.  **Tool-Calling:** Encourage the model to use its tools to find information rather than guessing.
    ```
    If you are not sure about file content or codebase structure pertaining to the user’s request, use your tools to read files and gather the relevant information: do NOT guess or make up an answer.
    ```
3.  **Planning (Optional but Recommended):** Induce the model to "think out loud" by planning and reflecting between tool calls. This improves performance on complex tasks.
    ```
    You MUST plan extensively before each function call, and reflect extensively on the outcomes of the previous function calls. DO NOT do this entire process by making function calls only, as this can impair your ability to solve the problem and think insightfully.
    ```

## 3. Long Context Prompts

GPT-4.1 supports a 1M token context window. To make the most of it:

-   **Prompt Organization:** For long context prompts, place your instructions at both the **beginning and the end** of the provided context for the best performance.
-   **Tune Context Reliance:** Explicitly tell the model how much it should rely on its internal knowledge versus the provided context.
    -   **Strictly Context:** `Only use the documents in the provided External Context to answer...`
    -   **Hybrid Approach:** `By default, use the provided external context... but if other basic knowledge is needed... you can use some of your own knowledge.`
-   **Data Delimiters:** When providing a large number of documents, use clear delimiters. XML and custom pipe-based formats perform well. JSON performs poorly for this task.
    -   **Good (XML):** `<doc id='1' title='Title'>Content...</doc>`
    -   **Good (Pipe):** `ID: 1 | TITLE: Title | CONTENT: Content...`
    -   **Poor (JSON):** `[{'id': 1, 'title': 'Title', 'content': 'Content...'}]`

## 4. Chain of Thought (CoT)

While not a reasoning model, GPT-4.1 can be prompted to produce a step-by-step plan (thinking out loud), which improves output quality.

-   **Basic CoT Prompt:** Start with a simple instruction at the end of your prompt.
    ```
    First, think carefully step by step about... Then, print out...
    ```
-   **Advanced CoT Strategy:** For more complex tasks, provide a more structured reasoning strategy for the model to follow.
    ```
    # Reasoning Strategy
    1. Query Analysis: Break down and analyze the query...
    2. Context Analysis: Carefully select and analyze relevant documents...
    3. Synthesis: Summarize which documents are most relevant and why...
    ```

## 5. Instruction Following

GPT-4.1's literal instruction following is a key strength.

-   **Recommended Workflow:**
    1.  Start with a high-level `# Instructions` section.
    2.  Add specific sub-sections (e.g., `# Sample Phrases`, `# Output Format`) for detailed guidance.
    3.  Use ordered lists for step-by-step workflows.
    4.  If issues persist, check for conflicting instructions, add examples, and use emphasis (like all-caps) sparingly.
-   **Avoid Common Pitfalls:**
    -   Overly strict rules (e.g., "you *must* call a tool") can lead to hallucinated inputs. Add fallback instructions (e.g., "if you don't have enough information, ask the user").
    -   Models can overuse sample phrases verbatim. Instruct them to vary the phrasing.

## 6. General Prompt Structure

A good starting point for structuring your prompts:

```markdown
# Role and Objective
[Define the AI's role and what it's supposed to achieve.]

# Instructions
[High-level rules and guidelines.]

## Sub-categories for more detailed instructions
[e.g., Tone, Formatting, Prohibited Topics]

# Reasoning Steps
[Define the step-by-step process the model should follow.]

# Output Format
[Specify the desired output structure, e.g., JSON, Markdown, XML.]

# Examples
[Provide clear examples of desired input/output.]

# Context
[Provide any relevant context, documents, or data.]

# Final instructions and prompt to think step by step
[Your final call to action and CoT prompt.]
```
