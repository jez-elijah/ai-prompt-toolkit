# AI Prompt Toolkit

Reusable prompt templates, a testing log, a plain-language guide to using AI safely, and a sample AI usage policy. Built as a learning and portfolio project by Jez Elijah Malinawan.

## Contents

| Path | What it is |
|---|---|
| `templates/` | Five reusable prompt templates with placeholders, rules, and an output format |
| `TESTING_LOG.md` | Test plan and results table for each template (fill in as you run them) |
| `docs/using-ai-safely-at-work.md` | A 1-2 page guide for non-technical colleagues |
| `docs/sample-ai-usage-policy.md` | A one-page draft AI usage policy (sample only) |

## How the templates are built

Each template has the same parts: a role, the task, the rules (including what the model must not do), the input placeholders in `{{double braces}}`, and a fixed output format. Fixed formats make outputs easy to check and easy to drop into a workflow or automation tool.

## How to test a template

1. Pick a test case from `TESTING_LOG.md`.
2. Fill the placeholders and run the prompt in the AI tool you are evaluating.
3. Record the result, what went wrong, and what you changed in the template.

## Limitations

- Template tests were run on one model (Claude Sonnet 5.5) and graded with that model's help, then reviewed by me, so grading may share the model's blind spots.
- Ten tests are enough to find obvious failures, not to measure reliability.
- The usage policy is a sample for learning and has not been reviewed by legal or compliance staff.

## Note

The policy is a sample written for learning purposes. It is not legal advice and is not any company's real policy.
