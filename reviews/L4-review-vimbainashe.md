**Reviewed:** Team 7 · `requirements/L3-test-basis.md` · commit ___
**Reviewer:** Vimbainashe Chidhau · **Date:** 18/11/2026
**Time spent on individual review:** _25_ minutes

## A. The five requirement defects

For each finding: quote the text, name the defect type, and say what you would ask the author.
Ask questions rather than writing corrections — a reviewer who rewrites somebody's requirement
has replaced the author's intent with their own, which is the failure the review exists to prevent.

| # | Quoted text | Defect type | Question for the author |
|---|-------------|-------------|-------------------------|
| 1 |(AC-1.1) "Given that the product catalogue contains a product with a matching name..." |Ambiguity  | Could you clarify what qualifies as a matching product name? Should the search return products containing the entered term anywhere in their names, or only products whose complete names match the search term? |
| 2 | (AC-1.5) "Every product displayed in the search results must match the submitted search term"|Ambiguity |Could you clarify how a product is considered to match the submitted search term? For example, should partial matches be accepted, or must the complete product name match? |
| 3 | (AC-1.4) "Given that the customer has entered a search term and selected a product category, when search is submitted, then the displayed products match both the search term and selected category." |Omission |What should happen if the search term matches existing products, but none of those products belong to the selected category? Should the website display a no-results message or another response? |



## B. Testability

Take four acceptance criteria at random and put each through the three questions from lecture 3.

| Criterion ID | Observable outcome? | One interpretation? | Finite pass/fail check? | If no — why |
|---|---|---|---|---|
|AC-1.1 |Yes |No |Yes, after clarification |The meaning of a matching product name is not fully defined |
|AC-1.3 |Yes |Yes |Yes | |
|AC-1.4 |Yes |Yes |Yes | |
|AC-1.5 |Yes |No |Yes, after clarification |The search matching rule does not specify whether partial matches are accepted. |

## C. Coverage of cases



| Story | Expected path | Boundary | Invalid case | Interaction with another rule |
|---|---|---|---|---|
| 1-Product Search |Yes |Yes |Yes |Yes |

Explanation:
- Expected path: AC-1.1 checks whether matching products are displayed.
- Boundary: AC-1.3 checks a search that matches exactly one product.
- Invalid case: AC-1.2 checks a search with no matching products.
- Interaction: AC-1.4 checks searching while a product category is selected.
The story also includes empty search behaviour and case-insensitive searching.

Assessment: Story 1 has good coverage of the main search scenarios.

## D. Test conditions

- [x] Conditions name what will be tested without prescribing steps, data or expected results.
- [x] Every condition traces back to a specific acceptance criterion.
- [x] Numbering is consistent and would survive a criterion being added later.
- [ ] At least one condition exists that the criteria did not obviously imply — a sign the author
      was deriving rather than transcribing.

## E. Open questions

- [x] The section exists and is not empty.
- [x] Each entry says what was assumed.
- [x]Each entry says why it matters.



## F. Decision

One of these, with a sentence of reasoning.

- [ ] **Accept** — usable as a test basis as it stands
- [x] **Accept with changes** — usable once the findings above are addressed
- [ ] **Rework** — the defects are structural rather than local

_Reasoning:_ Team 07 has provided three user stories with acceptance criteria and related test conditions. Most criteria are understandable and testable, and the test basis covers expected user interactions. However, some issues need clarification before the test basis can be accepted without changes. These include ambiguous wording in the product search requirements, the contradiction between the maximum cart quantity of 10 in AC-2.2 and 99 in TC-2.2.2, and assumptions in the open questions that are not yet confirmed. Some test conditions also need clearer wording to ensure they can be tested consistently.

## G. One thing done well

Team 07 has provided a good range of acceptance criteria covering both normal and exceptional user behaviour. For example, the product search story includes no-results handling, case-insensitive searches, category filtering, and empty searches. This gives testers several different scenarios to verify rather than focusing only on the successful search path.
