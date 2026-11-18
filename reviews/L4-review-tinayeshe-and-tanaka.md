**Reviewed:** app-testing-team-7 · `requirements/L3-test-basis.md` · commit 2156b26
**Reviewers:** Tinayeshe Mugwagwa and Tanaka Zindi · **Date:** 18.11.2026
**Time spent on review:** 25 minutes

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
| 8 | "the website requires them to register or log in before allowing the operation" (AC-3.3) vs "The website provides an authentication prompt or explanatory message." (TC-3.3.2) | ambiguity | Is the visitor sent to the login page, or only shown a message? And after they log in, is the product added to favourites automatically, or must they add it again? |

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
| 3 | ✓ AC-3.1, AC-3.2, AC-3.6 | ✓ AC-3.4 | ✓ AC-3.3 | ✓ AC-3.5 |

## D. Test conditions

- [x] Conditions name what will be tested without prescribing steps, data or expected results
- [x] Every condition traces back to a specific acceptance criterion
- [x] Numbering is consistent and would survive a criterion being added later
- [x] At least one condition exists that the criteria did not obviously imply — a sign the author
      was deriving rather than transcribing (TC-2.5.2 other products stay in the cart; TC-2.6.2 zero-quantity products stay removed after refresh)

Notes:
- TC-2.2.2 uses a maximum of 99 while its source AC-2.2 says 10, so that condition does not match the criterion it traces to.
- TC-3.4.2 requires "an appropriate message when a duplicate favourite is attempted", but AC-3.4 only says the product must not appear twice. Should AC-3.4 require a message, and what message?
- Further derived conditions: TC-3.1.2 (the confirmation must match a real success) and TC-3.6.2 (removing one favourite keeps the others).

## E. Open questions

- [x] The section exists and is not empty
- [x] Each entry says what was assumed, not only what was unclear
- [x] Each entry says why it matters

Notes: Open question 1 assumes a maximum of 99, but AC-2.2 states 10, so the assumption has not been carried into the criteria consistently (finding 1). Open question 5 assumes a rejection message that AC-2.3 does not require (finding 3). Open question 6 (email verification before using favourites) is still unresolved, and no criterion in Story 3 covers a logged-in but unverified account. The entries do not say which story or criterion they relate to.

## F. Decision

Decision: Accept with changes
Reason:
Team 07 has provided three user stories with acceptance criteria and related test conditions. Most criteria are understandable and testable, and the test basis covers expected user interactions. However, some issues need clarification before the test basis can be accepted without changes. These include ambiguous wording in the product search requirements, the contradiction between the maximum cart quantity of 10 in AC-2.2 and 99 in TC-2.2.2, and assumptions in the open questions that are not yet confirmed. Some test conditions also need clearer wording to ensure they can be tested consistently.

## G. One thing done well

Team 07 has provided a good range of acceptance criteria covering both normal and exceptional user behaviour. For example, the product search story includes no-results handling, case-insensitive searches, category filtering, and empty searches. This gives testers several different scenarios to verify rather than focusing only on the successful search path.
