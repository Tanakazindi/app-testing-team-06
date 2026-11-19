**Reviewed:** Team 07 · `requirements/L3-test-basis.md` · commit 8a7a54f
**Reviewer:** Tanya · **Date:** 19 November 2026
**Time spent on individual review:** 25 minutes

# A. The five requirement defects

For each finding: quote the text, name the defect type, and say what you would ask the author. Ask questions rather than writing corrections.

| # | Quoted text | Defect type | Question for the author |
|---|---|---|---|
| 1 | (AC-2.2) "The maximum quantity allowed in a single cart item is 10." vs (TC-2.2.2) "The quantity cannot exceed the defined maximum of 99." | Contradiction | Your acceptance criterion states a maximum quantity of 10, but your test condition tests for a maximum of 99. Which is the correct business rule we should be testing against? |
| 2 | (AC-1.1) "Given that the product catalogue contains a product with a matching name..." | Ambiguity | Could you clarify what qualifies as a "matching name"? Should a search for "hammer" return a "claw hammer", or only products named exactly "hammer"? |
| 3 | (AC-3.4) "Given that a product is already in the customer's favourites, when the customer attempts to add the same product again, then the product does not appear more than once in the favourites list." | Omission | What should happen visually when the customer clicks "add to favourites" a second time? Should the button be disabled, or should a specific error message appear? |

# B. Testability

Take four acceptance criteria at random and put each through the three questions.

| Criterion ID | Observable outcome? | One interpretation? | Finite pass/fail check? | If no — why |
|---|---|---|---|---|
| AC-1.2 | Yes | Yes | Yes | No issue found. |
| AC-2.3 | Yes | Yes | Yes | No issue found. |
| AC-3.1 | Yes | No | No | The phrase "confirmation that the operation was successful" is ambiguous. What form does this confirmation take? Is it a pop-up, a banner, or a text change? |
| AC-3.3 | Yes | Yes | Yes | No issue found. |

# C. Coverage of cases

| Story | Expected path | Boundary | Invalid case | Interaction with another rule |
|---|---|---|---|---|
| Story 1 (Search) | Yes | Yes | Yes | Yes |
| Story 2 (Cart) | Yes | Yes | Yes | Yes |
| Story 3 (Favourites) | Yes | Yes | Yes | Yes |

*Explanation: The test basis shows good overall coverage. For example, Story 2 includes the expected path (adding an item), a boundary (maximum quantity limit), and an invalid case (adding a negative quantity).*

# D. Test conditions

- [x] Conditions name what will be tested without prescribing steps, data or expected results.
- [x] Every condition traces back to a specific acceptance criterion.
- [ ] Numbering is consistent and would survive a criterion being added later.
- [x] At least one condition exists that the criteria did not obviously imply.

*Note on numbering: The numbering in Story 2 (TC-2.2.2) contradicts the AC numbering rule and will need to be fixed alongside the contradiction found in Section A.*

# E. Open questions

- [x] The section exists and is not empty.
- [x] Each entry says what was assumed.
- [x] Each entry says why it matters.

# F. Decision

*(See consolidated team record in `L4-review-record.md` for the team decision.)*
