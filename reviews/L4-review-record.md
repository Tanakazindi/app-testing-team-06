# L4 Review Record — Team 06 reviewing Team 07

**Consolidated by:** Team 06
**Reviewed Document:** Team 07 `requirements/L3-test-basis.md`

## Consolidated Findings

*This record consolidates the individual findings from our team members. Independent agreement is noted where multiple reviewers found the same issue.*

| # | Quoted text | Defect type | Question for the author | Found independently by |
|---|---|---|---|---|
| 1 | (AC-1.1) "Given that the product catalogue contains a product with a matching name..." | Ambiguity | Could you clarify what qualifies as a matching product name? Should the search return products containing the entered term anywhere in their names, or only products whose complete names match the search term? | Vimbainashe |
| 2 | (AC-1.5) "Every product displayed in the search results must match the submitted search term" | Ambiguity | Could you clarify how a product is considered to match the submitted search term? For example, should partial matches be accepted, or must the complete product name match? | Vimbainashe |
| 3 | (AC-1.4) "Given that the customer has entered a search term and selected a product category, when search is submitted, then the displayed products match both the search term and selected category." | Omission | What should happen if the search term matches existing products, but none of those products belong to the selected category? Should the website display a no-results message or another response? | Vimbainashe |
| 4 | (AC-2.2 vs TC-2.2.2) Maximum cart quantity contradiction | Contradiction | AC-2.2 implies a maximum cart quantity of 10, but TC-2.2.2 tests a quantity of 99. Which is the correct maximum limit for the cart? | Vimbainashe |

## Section B: Testability Summary
*(Based on individual reviews)*
- AC-1.1 and AC-1.5 fail the "One interpretation" check due to ambiguous matching rules. 
- Other checked criteria (AC-1.3, AC-1.4) pass the testability checks.

## Section C: Coverage Summary
- **Story 1 (Product Search):** Good coverage. Includes expected path (AC-1.1), boundary (AC-1.3), invalid case (AC-1.2), and interaction (AC-1.4).

## Section D: Test conditions
- Conditions are generally well-written but require tracing back to resolve the ambiguity in AC-1.1 and AC-1.5.

## Section E: Open questions
- The section exists, but some assumptions need clearer wording to ensure they can be tested consistently.

## F. Decision

**Decision:** Accept with changes 

**Reasoning:** Team 07 has provided three user stories with acceptance criteria and related test conditions. Most criteria are understandable and testable, and the test basis covers expected user interactions. However, some issues need clarification before the test basis can be accepted without changes. These include ambiguous wording in the product search requirements, the contradiction between the maximum cart quantity of 10 in AC-2.2 and 99 in TC-2.2.2, and assumptions in the open questions that are not yet confirmed. Some test conditions also need clearer wording to ensure they can be tested consistently.

## G. One thing done well

Team 07 has provided a good range of acceptance criteria covering both normal and exceptional user behaviour. For example, the product search story includes no-results handling, case-insensitive searches, category filtering, and empty searches. This gives testers several different scenarios to verify rather than focusing only on the successful search path.
