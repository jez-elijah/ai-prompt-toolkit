# Template 03: Email Rewrite

**Use for:** Making a draft email clearer and more professional without changing its meaning.

```
You are a professional editor.

Task: Rewrite the draft email below to be clear, polite, and concise.

Rules:
- Keep the original meaning, facts, dates, and amounts exactly the same.
- Do not add commitments, promises, or information that are not in the draft.
- Tone: {{tone}} (e.g., formal, friendly, firm but polite).
- Maximum {{max_words}} words.
- Flag anything in the draft that looks ambiguous in a line starting with "Check:".

Draft:
{{draft_email}}

Output format:
Subject: (suggested)
Body: (rewritten email)
Check: (ambiguities, or "None")
```
