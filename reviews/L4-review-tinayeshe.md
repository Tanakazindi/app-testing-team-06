**Reviewed:** Team 07 · `requirements/L3-test-basis.md` · commit 2156b26
**Reviewers:** Tinayeshe Mugwagwa and Tanaka Zindi · **Date:** 18.11.2026
**Time spent on review:** ___ minutes

*Reviewed jointly by Tinayeshe Mugwagwa and Tanaka Zindi; the findings below were not produced independently.*

## A. The five requirement defects

For each finding: quote the text, name the defect type, and say what you would ask the author.
Ask questions rather than writing corrections — a reviewer who rewrites somebody's requirement
has replaced the author's intent with their own, which is the failure the review exists to prevent.

| # | Quoted text | Defect type | Question for the author |
|---|-------------|-------------|-------------------------|
| 1 | "The maximum quantity allowed in a single cart item is 10." (AC-2.2) vs "The quantity cannot exceed the defined maximum of 99." (TC-2.2.2) and "A maximum of 99 units per product is assumed" (Open question 1) | contradiction | Which maximum applies to one cart item, 10 or 99? |
| 2 | "The maximum quantity allowed in a single cart item is 10." (AC-2.2) | omission | What should happen when the customer clicks plus at the maximum, or types a larger number: is the button disabled, is a message shown, or is the value reset? |
| 3 | "then the product is not added to the shopping cart" (AC-2.3) vs "The customer should be informed why the quantity was rejected" (Open question 5) | omission | Should AC-2.3 also require a message explaining the rejection, as Open question 5 assumes? If so, what should the message say? |
| 4 | "when the customer adds it to the shopping cart, then the product appears in the cart with an initial quantity of one" (AC-2.1) | omission | What should happen when the customer adds a product that is already in the cart: is its quantity increased, or does a second line appear? |
| 5 | "then the matching product is displayed" (AC-1.1) and "Every product displayed in the search results must match the submitted search term" (AC-1.5) | ambiguity | Does "match" mean the full product name, or any product whose name contains the term (e.g. "plier" finding "Combination Pliers")? |
| 6 | "the website informs the customer that no matching products were found" (AC-1.2) and "An appropriate no-results message is displayed" (TC-1.2.2) | unverifiable | What message text, or what kind of message, counts as "appropriate", so a tester can say pass or fail? |
| 7 | "Search results display the correct product information." (TC-1.1.2) | unverifiable | Which product information (name, price, image, stock?) must be shown, and correct compared with what? |

*Aim for three to six findings. Fewer than three usually means you skimmed; more than eight
usually means you are listing preferences rather than defects.*

## B. Testability

Take four acceptance criteria at random and put each through the three questions from lecture 3.

| Criterion ID | Observable outcome? | One interpretation? | Finite pass/fail check? | If no — why |
|---|---|---|---|---|
| AC-1.2 | Yes | No | No | The form and wording of the "no matching products" message is not stated (finding 6). |
| AC-1.6 | Yes | Yes | Yes | — |
| AC-2.2 | Yes | No | No | The maximum conflicts with TC-2.2.2 and Open question 1 (10 vs 99), and no result is stated for exceeding it (findings 1–2). |
| AC-2.4 | Yes | No | Yes | "Subtotal" could mean the line total for one product or the total of all products before other charges. |

## C. Coverage of cases

Does each story go beyond the happy path?

| Story | Expected path | Boundary | Invalid case | Interaction with another rule |
|---|---|---|---|---|
| 1 | ✓ AC-1.1 | ✓ AC-1.3, AC-1.7 | ✓ AC-1.2 | ✓ AC-1.4 |
| 2 | ✓ AC-2.1, AC-2.5 | ✓ AC-2.2 (no behaviour stated at the limit) | ✓ AC-2.3 | ✓ AC-2.4 |
| 3 | | | | |

## D. Test conditions

- [x] Conditions name what will be tested without prescribing steps, data or expected results
- [x] Every condition traces back to a specific acceptance criterion
- [x] Numbering is consistent and would survive a criterion being added later
- [x] At least one condition exists that the criteria did not obviously imply — a sign the author
      was deriving rather than transcribing (TC-2.5.2 other products stay in the cart; TC-2.6.2 zero-quantity products stay removed after refresh)

Note: TC-2.2.2 uses a maximum of 99 while its source AC-2.2 says 10, so that condition does not match the criterion it traces to.

## E. Open questions

- [x] The section exists and is not empty
- [x] Each entry says what was assumed, not only what was unclear
- [x] Each entry says why it matters

Notes: Open question 1 assumes a maximum of 99, but AC-2.2 states 10, so the assumption has not been carried into the criteria consistently (finding 1). Open question 5 assumes a rejection message that AC-2.3 does not require (finding 3). The entries do not say which story or criterion they relate to.

## F. Decision

(Filled in the team record in Step 2.)

## G. One thing done well

(Filled in the team record in Step 2.)
