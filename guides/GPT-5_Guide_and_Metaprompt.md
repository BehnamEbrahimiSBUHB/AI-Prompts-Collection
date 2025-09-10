
# The Definitive Guide to Prompting GPT-5

## Core Prompting Principles

### Instruction Following
GPT-5 follows prompt instructions with surgical precision. This means that poorly-constructed prompts with contradictory or vague instructions can be more damaging to GPT-5 than to other models, as it expends reasoning tokens searching for a way to reconcile the contradictions rather than picking one instruction at random.

**Best Practice:**
- Ensure that your prompts are internally consistent and that all instructions are unambiguous.
- For complex tasks, break down the instructions into a clear hierarchy.
- If you notice the model is struggling, review your prompt for hidden contradictions.

### Steering
GPT-5 is highly steerable and receptive to prompt instructions surrounding verbosity, tone, and tool calling behavior.

**Best Practice:**
- Use the `verbosity` parameter to control the length of the model's final answer.
- For specific contexts where you might want the model to deviate from the global default, you can use natural-language verbosity overrides in the prompt.

### Avoiding Contradictions
It is crucial to avoid contradictions in your prompts. For example, do not ask the model to never do something and then provide an exception in the same prompt.

**Example of a contradictory prompt:**
```
Never schedule an appointment without explicit patient consent recorded in the chart.
...
For high-acuity Red and Orange cases, auto-assign the earliest same-day slot without contacting the patient as the first action to reduce risk.
```

**Best Practice:**
- Review your prompts carefully to ensure that there are no conflicting instructions.
- If you need to provide exceptions to a rule, make sure that the exceptions are clearly defined and do not contradict the main rule.

## New API Features & Parameters

### Verbosity Parameter
The `verbosity` parameter allows you to control the length and detail of the model's output. It accepts three values: `low`, `medium`, and `high`.

- **low:** Terse UX, minimal prose.
- **medium (default):** Balanced detail.
- **high:** Verbose, great for audits, teaching, or hand-offs.

**Example:**
```python
response = client.responses.create(
    model="gpt-5-mini",
    input="Write a poem about a boy and his first pet dog.",
    text={"verbosity": "low"}
)
```

### Freeform Function Calling
GPT-5 can send raw text payloads to your custom tool without wrapping the data in JSON. This is useful for interacting with external runtimes such as code sandboxes, SQL databases, and shell environments.

**Example:**
```python
response = client.responses.create(
    model="gpt-5-mini",
    input="Please use the code_exec tool to calculate the area of a circle with radius equal to the number of 'r's in strawberry",
    text={"format": {"type": "text"}},
    tools=[
        {
            "type": "custom",
            "name": "code_exec",
            "description": "Executes arbitrary python code",
        }
    ]
)
```

### Context-Free Grammar (CFG)
CFGs allow you to constrain the model's output to a specific format. This is useful for generating code, SQL queries, and other structured data.

**Example:**
```python
response_mssql = client.responses.create(
    model="gpt-5",
    input=sql_prompt_mssql,
    text={"format": {"type": "text"}},
    tools=[
        {
            "type": "custom",
            "name": "mssql_grammar",
            "description": "Executes read-only Microsoft SQL Server queries...",
            "format": {
                "type": "grammar",
                "syntax": "lark",
                "definition": mssql_grammar
            }
        },
    ],
    parallel_tool_calls=False
)
```

### Minimal Reasoning
The `minimal` reasoning effort runs GPT-5 with few or no reasoning tokens to minimize latency and speed up time-to-first-token. This is ideal for deterministic, lightweight tasks where explanations aren’t needed.

**Example:**
```python
response = client.responses.create(
    model="gpt-5",
    input= [
        { 'role': 'developer', 'content': "Classify sentiment... Return one word only." },
        { 'role': 'user', 'content': 'The food at the restaurant was great! ...' }
    ],
    reasoning = {
        "effort": "minimal"
    },
)
```

## Advanced Agentic Workflows

### Controlling Agentic Eagerness
You can control how proactive or cautious the model is in its agentic behavior.

- **For less eagerness:** Use a lower `reasoning_effort` and provide clear criteria for exploration and early stopping.
- **For more eagerness:** Use a higher `reasoning_effort` and provide prompts that encourage persistence and autonomy.

### Tool Preambles
GPT-5 can provide clear upfront plans and consistent progress updates via “tool preamble” messages. You can steer the frequency, style, and content of these preambles in your prompt.

### Responses API
Use the Responses API and the `previous_response_id` to allow the model to refer to its previous reasoning traces, conserving CoT tokens and eliminating the need to reconstruct a plan from scratch after each tool call.

## Frontend Development

GPT-5 is excellent at building applications in one shot. For new apps, we recommend using the following frameworks and packages to get the most out of the model's frontend capabilities:

- **Frameworks:** Next.js (TypeScript), React, HTML
- **Styling / UI:** Tailwind CSS, shadcn/ui, Radix Themes
- **Icons:** Material Symbols, Heroicons, Lucide
- **Animation:** Motion
- **Fonts:** San Serif, Inter, Geist, Mona Sans, IBM Plex Sans, Manrope

## Prompt Optimization

The GPT-5 Prompt Optimizer is a tool that helps you improve your existing prompts and migrate them for use with GPT-5. The optimizer can help you to:

- Remove contradictions in your prompt instructions.
- Add missing or unclear format specifications.
- Fix inconsistencies between the prompt and few-shot examples.

---

# Metaprompt for Optimal GPT-5 Performance

```
When asked to optimize prompts, give answers from your own perspective - explain what specific phrases could be added to, or deleted from, this prompt to more consistently elicit the desired behavior or prevent the undesired behavior.

Here's a prompt: [PROMPT]

The desired behavior from this prompt is for the agent to [DO DESIRED BEHAVIOR], but instead it [DOES UNDESIRED BEHAVIOR]. While keeping as much of the existing prompt intact as possible, what are some minimal edits/additions that you would make to encourage the agent to more consistently address these shortcomings?
```
