**Reviewed:** app-testing-team-07 · `requirements/L3-test-basis.md` · commit 2156b26
**Reviewer:** Tinayeshe Mugwagwa and Tanaka Zindi· **Date:** 18.11.2026
**Time spent on individual review:** 25 minutes

## A. The five requirement defects

For each finding: quote the text, name the defect type, and say what you would ask the author.
Ask questions rather than writing corrections — a reviewer who rewrites somebody's requirement
has replaced the author's intent with their own, which is the failure the review exists to prevent.

| # | Quoted text | Defect type | Question for the author |
|---|-------------|-------------|-------------------------|
| 1 | "The maximum quantity allowed in a single cart item is 10." (AC-2.2) vs "The quantity cannot exceed the defined maximum of 99." (TC-2.2.2) | contradiction | Which maximum applies to one cart item, 10 or 99? |
| 2 | "The maximum quantity allowed in a single cart item is 10." (AC-2.2) | omission | What should happen when the customer clicks plus at 10, or types 11: is the button disabled, is a message shown, or is the value reset to 10? |
| 3 | "A product with a quantity of zero must not remain displayed as an active item" (AC-2.6) vs "Products with zero quantity are completely removed" (TC-2.6.1) | ambiguity | Does "not displayed as an active item" mean the product is removed from the cart, or could it stay visible as inactive (e.g. greyed out)? |
| 4 | "then the product appears in the cart with an initial quantity of one and its correct price" (AC-2.1) | ambiguity | What is the "correct price" compared against: the catalogue price on the product page, or a price after any discount? |
| 5 | "when the customer adds it to the shopping cart, then the product appears in the cart with an initial quantity of one" (AC-2.1) | omission | What should happen when the customer adds a product that is already in the cart: is its quantity increased, or does a second line appear? |
| 6 | "then the cart subtotal and overall total are recalculated" (AC-2.4) | ambiguity | Does "subtotal" mean the line total for that product, or the total of all products before other charges? |

*Aim for three to six findings. Fewer than three usually means you skimmed; more than eight
usually means you are listing preferences rather than defects.*

## B. Testability

Take four acceptance criteria at random and put each through the three questions from lecture 3.

| Criterion ID | Observable outcome? | One interpretation? | Finite pass/fail check? | If no — why |
|---|---|---|---|---|
| AC-2.1 | Yes | No | Yes | "Correct price" is not defined (finding 4). |
| AC-2.2 | Yes | No | No | The maximum conflicts with TC-2.2.2 (10 vs 99), and no result is stated for exceeding it, so a test at 11 has no expected outcome (findings 1–2). |
| AC-2.4 | Yes | No | Yes | "Subtotal" can mean the line total or the cart subtotal (finding 6). |
| AC-2.5 | Yes | Yes | Yes | — |

## C. Coverage of cases

Does each story go beyond the happy path?

| Story | Expected path | Boundary | Invalid case | Interaction with another rule |
|---|---|---|---|---|
| 1 | | | | |
| 2 | ✓ AC-2.1, AC-2.5 | ✓ AC-2.2 (no behaviour stated at the limit) | ✓ AC-2.3 | ✓ AC-2.4 |
| 3 | | | | |

## D. Test conditions

- [x] Conditions name what will be tested without prescribing steps, data or expected results
- [x] Every condition traces back to a specific acceptance criterion
- [x] Numbering is consistent and would survive a criterion being added later
- [x] At least one condition exists that the criteria did not obviously imply — a sign the author
      was deriving rather than transcribing (TC-2.5.2 other products stay; TC-2.6.2 after refresh)

Note: TC-2.2.2 uses a maximum of 99 while its source AC-2.2 says 10, so that condition does not match the criterion it traces to.

## E. Open questions

- [ ] The section exists and is not empty
- [ ] Each entry says what was assumed, not only what was unclear
- [ ] Each entry says why it matters

*An empty open-questions section on an undocumented product is a finding in itself. Record it.*

## F. Decision

(Filled in the team record in Step 2.)

## G. One thing done well

(Filled in the team record in Step 2.)
