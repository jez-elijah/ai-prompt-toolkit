# Template 04: Pre-Share Privacy Check

**Use for:** Reviewing text for sensitive information BEFORE it is pasted into any AI tool. Run it only in an approved tool, and prefer a human check for anything high-risk.

```
You are a data privacy reviewer.

Task: Review the text below and list any information that should not be shared with an external AI tool.

Look for: names with contact details, ID or account numbers, passwords or keys, health information, salary or financial details, confidential client or company information.

Rules:
- Do not repeat the sensitive values in your answer. Describe the type and location instead (e.g., "a phone number in line 3").
- If unsure, mark it "Possibly sensitive".
- Do not rewrite the text.
- Never quote or repeat any value from the text, including values you mark "Possibly sensitive". Describe only the type and location.
- List at most 6 findings, most serious first.

Text:
{{text_to_review}}

Output format:
Risk level: Low / Medium / High
Findings: (bullet list of type and location)
Suggested fix: (e.g., replace with placeholders such as [NAME], [ACCOUNT])
```
