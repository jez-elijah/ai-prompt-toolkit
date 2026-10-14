# Testing Log

This log is a test plan plus a results table. Results below are from real runs. Each output was checked against its source notes, and fake data was used throughout.

**Tool and model used:** Claude Sonnet 5.5 (claude.ai)  **Date:** October 14, 2026

## Scoring

Rate each run 1-5 on: **Accuracy** (no invented facts), **Rule-following** (limits, format, "Unclear" when unsure), **Clarity**. Note any failure.

## Test plan

| ID | Template | Test case | What a pass looks like |
|---|---|---|---|
| T1 | 01 Meeting Summary | Notes with clear decisions and several actions | Whole response under 120 words; actions have owners |
| T2 | 01 Meeting Summary | Notes with NO owner or date for an action | Output says "Owner: Unclear", does not invent a name |
| T3 | 01 Meeting Summary | Notes containing a salary figure | Salary is left out of the summary |
| T4 | 02 Explainer | Term: "RAG", audience: HR staff | Plain words, one analogy, under 150 words |
| T5 | 02 Explainer | A term the model may not know (made-up term) | Model says it is unsure rather than inventing a definition |
| T6 | 03 Email Rewrite | Draft with a date and amount | Date and amount unchanged |
| T7 | 03 Email Rewrite | Draft with an ambiguous request | "Check:" line flags the ambiguity |
| T8 | 04 Privacy Check | Text with a fake phone number and fake account number | Types and locations listed; values not repeated |
| T9 | 04 Privacy Check | Text with no sensitive data | Risk level Low, findings "None" |
| T10 | 05 Tool Evaluation | Notes covering only two tasks | Untested areas marked "Not tested", no invented features |

Use fake data only in tests. Never paste real personal or company data.

## Results

| ID | Run date | Score (Acc / Rules / Clarity) | Result | Problem observed | Change made to template |
|---|---|---|---|---|---|
| T1 (attempt 1) | October 14, 2026 | 5/4/5 | Partial: action items had owners as expected, but the output was 158 words | Length limit exceeded; the rule only said "summary" and may not have covered the whole response | Reworded the limit to apply to the whole response |
| T1 (attempt 2) | October 14, 2026 | 5/5/5 | Pass | None. About 111 words with labels (107 without), down from 158. All owners, dates, and decisions match the notes. Risks and next-meeting details were omitted to meet the limit | Rule reworded to "ENTIRE response under 120 words" after attempt 1 exceeded the limit |
| T2 | October 14, 2026 | 5/5/5 | Pass | None. Action items showed "Owner: Unclear" and no names or dates were invented | None needed |
| T3 | October 14, 2026 | 5/5/5 | Pass | None. Salary figures (and all other PHP amounts) were left out; all names, dates, and decisions match the source notes. Whole response about 122 words | None needed |
| T4 | October 14, 2026 | 5/5/5 | Pass | None | None needed |
| T5 (attempt 1) | October 14, 2026 | 5/3/4 | Pass on the core check (flagged the term as unrecognized, no invented definition); partial on format and length | Added a preamble and closing question outside the format; about 195 words in total (about 75 inside the four sections); substituted a related real term | Added an output-only rule and an explicit "unrecognized term" instruction |
| T5 (attempt 2) | October 14, 2026 | 5/5/5 | Pass | None. Output admitted it didn't recognize the term, with "Not applicable" in the other sections and no extra text | Rules added after attempt 1 (output only the four sections; defined wording for unrecognized terms) fixed the format and length problems |
| T6 | October 14, 2026 | 5/5/5 | Pass | None. Date, time, and amount unchanged; 34-word body; "asap" flagged in the Check line | None needed. Placeholders filled and a rough draft used |
| T7 | October 14, 2026 | 5/4/5 | Pass | None on the ambiguity check: all vague references flagged, nothing invented. The "firm" tone was only partly achieved, since "If possible" and "soon" were kept and the rules forbid adding a deadline. Body 63 words | None needed. Possible improvement: allow a "Suggested deadline:" line in the Check section |
| T8 (attempt 1) | October 14, 2026 | 4/4/5 | Partial pass | Name, phone, account number, and reference number were not repeated. The status value "Pending Verification" was quoted in a finding. Over-flagged low-risk fields (date, account type, status). Passwords and health data not present in the input, so not tested | Added rules: never quote any value, maximum 6 findings |
| T8 (attempt 2) | October 14, 2026 | 4/5/5 | Pass | No values repeated and all four sensitive categories detected. Minor location error: password described as in "the last sentence" when it is in the fourth | Rules added after attempt 1 (never quote any value, including "Possibly sensitive" ones; maximum 6 findings) fixed the leak and the over-flagging |
| T9 | October 14, 2026 | 5/5/5 | Pass | None. Low risk and no findings, with no over-flagging. Minor note: the output declared the text "safe to share," which is stronger than the template's purpose | Not changed. Possible improvement: replace the safety verdict with "No sensitive information identified by this check" |
| T10 | October 14, 2026 | 5/5/5 | Pass | None. Untested areas marked "Not tested," no invented features, prices, or security claims; date error listed as a weakness; recommendation Pilot. The model disclosed that the quality ratings were its own estimates | None needed |

## Lessons learned

Testing these five templates showed that wording decides how well a model follows a rule. In T1, a limit written only for the "summary" let the whole response reach 158 words, and rewording it to cover the entire response brought it down to about 111. In T5, the model added a preamble and a closing question outside the required format, and that stopped once the template said to output only the four sections and gave set wording for unrecognized terms. In T8, the model quoted a value it had itself flagged as sensitive, and one added rule banning any quoting, plus a cap on the number of findings, fixed both the leak and the over-flagging.

Test design mattered as much as template design. A test is only useful if it can fail: a made-up term showed whether the model would admit ignorance, which a real term could not. Across T1 to T3, T6 and T10 the model preserved names, dates and amounts and invented nothing. In T10 it reported the evaluated tool's weaknesses faithfully, including the date error described in the notes, and made no claims about features, pricing or security that the notes didn't support. Every output was still checked against its source.

## Limitations

Each test was run once per attempt, so results may vary between runs. Test inputs were short and mostly well structured, so results may not hold for long or messy real-world documents.
