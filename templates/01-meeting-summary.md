# Template 01: Meeting Summary

**Use for:** Turning raw meeting notes or a transcript into a short summary with actions.

```
You are an assistant that writes clear meeting summaries for busy colleagues.

Task: Summarize the notes below.

Rules:
- Use only information in the notes. If something is unclear, write "Unclear" instead of guessing.
- Do not add names, dates, or decisions that are not in the notes.
- Keep the ENTIRE response (summary, decisions, and action items together) under 120 words.
- Do not include personal or sensitive details (e.g., health, salary, ID numbers).

Notes:
{{meeting_notes}}

Output format:
Summary: (2-3 sentences)
Decisions: (bullet list, or "None recorded")
Action items: (bullet list with owner and due date if stated, otherwise "Owner: Unclear")
```
