**Reviewed:** Team 7 · `requirements/L3-test-basis.md` · commit ___
**Reviewer:** Vimbaainashe Chidhau · **Date:** 18/11/2026
**Time spent on individual review:** ___ minutes

## A. The five requirement defects

For each finding: quote the text, name the defect type, and say what you would ask the author.
Ask questions rather than writing corrections — a reviewer who rewrites somebody's requirement
has replaced the author's intent with their own, which is the failure the review exists to prevent.

| # | Quoted text | Defect type | Question for the author |
|---|-------------|-------------|-------------------------|
| 1 | | ambiguity / contradiction / omission / unverifiable / gold plating | |
| 2 | | | |
| 3 | | | |

*Aim for three to six findings. Fewer than three usually means you skimmed; more than eight
usually means you are listing preferences rather than defects.*

## B. Testability

Take four acceptance criteria at random and put each through the three questions from lecture 3.

| Criterion ID | Observable outcome? | One interpretation? | Finite pass/fail check? | If no — why |
|---|---|---|---|---|
| | | | | |
| | | | | |
| | | | | |
| | | | | |

## C. Coverage of cases

Does each story go beyond the happy path?

| Story | Expected path | Boundary | Invalid case | Interaction with another rule |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |

## D. Test conditions

- [ ] Conditions name what will be tested without prescribing steps, data or expected results
- [ ] Every condition traces back to a specific acceptance criterion
- [ ] Numbering is consistent and would survive a criterion being added later
- [ ] At least one condition exists that the criteria did not obviously imply — a sign the author
      was deriving rather than transcribing

## E. Open questions

- [ ] The section exists and is not empty
- [ ] Each entry says what was assumed, not only what was unclear
- [ ] Each entry says why it matters

*An empty open-questions section on an undocumented product is a finding in itself. Record it.*

## F. Decision

One of these, with a sentence of reasoning.

- [ ] **Accept** — usable as a test basis as it stands
- [ ] **Accept with changes** — usable once the findings above are addressed
- [ ] **Rework** — the defects are structural rather than local

_Reasoning:_

## G. One thing done well

Be specific. "Good document" is not a review.
