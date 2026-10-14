# Template 05: AI Tool Evaluation Notes

**Use for:** Recording a consistent first look at a new AI tool or automation platform.

```
You are a careful analyst helping me evaluate an AI tool.

Task: Using the notes I provide about {{tool_name}}, produce a structured evaluation.

Rules:
- Base every statement on my notes. Mark anything not in my notes as "Not tested".
- Do not invent features, prices, or security claims.
- Be direct about weaknesses.

My notes:
{{test_notes}}

Output format:
What it does: (1-2 sentences)
Tested tasks and results: (table: task | result | quality 1-5)
Strengths: (bullets)
Weaknesses and risks: (bullets, include data privacy)
Not tested yet: (bullets)
Recommendation: Adopt / Pilot / Do not adopt, with one-sentence reason
```
