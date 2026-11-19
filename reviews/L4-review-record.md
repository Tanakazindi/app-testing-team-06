# L4 Review Record — Team 06 reviewing Team 07

**Consolidated by:** Team 06
**Reviewed Document:** Team 07 `requirements/L3-test-basis.md` (Commit 2156b26)

## Consolidated Findings

*This record consolidates the individual findings from our team members. Independent agreement is noted where multiple reviewers found the same issue.*

| # | Quoted text | Defect type | Question for the author | Found independently by |
|---|---|---|---|---|
| 1 | "The maximum quantity allowed in a single cart item is 10." (AC-2.2) vs "The quantity cannot exceed the defined maximum of 99." (TC-2.2.2) | Contradiction | Which maximum applies to one cart item, 10 or 99? | Tanya, Vimbainashe, Tinayeshe & Tanaka |
| 2 | (AC-1.1) "Given that the product catalogue contains a product with a matching name..." | Ambiguity | Does "match" mean the full product name, or any product whose name contains the term (e.g. "plier" finding "Combination Pliers")? | Tanya, Vimbainashe, Tinayeshe & Tanaka |
| 3 | (AC-1.4) "Given that the customer has entered a search term and selected a product category... then the displayed products match both..." | Omission | What should happen if the search term matches existing products, but none belong to the selected category? Should the website display a no-results message? | Vimbainashe |
| 4 | "The maximum quantity allowed in a single cart item is 10." (AC-2.2) | Omission | What should happen when the customer clicks plus at the maximum: is the button disabled, is a message shown, or is the value reset? | Tinayeshe & Tanaka |
| 5 | "when the customer adds it to the shopping cart, then the product appears in the cart with an initial quantity of one" (AC-2.1) | Omission | What should happen when the customer adds a product that is already in the cart: is its quantity increased, or does a second line appear? | Tinayeshe & Tanaka |
| 6 | "the website informs the customer that no matching products were found" (AC-1.2) and "An appropriate no-results message is displayed" (TC-1.2.2) | Unverifiable | What message text, or what kind of message, counts as "appropriate", so a tester can say pass or fail? | Tinayeshe & Tanaka |
| 7 | "then the product is not added to the shopping cart" (AC-2.3) vs "The customer should be informed why the quantity was rejected" (Open question 5) | Omission | Should AC-2.3 also require a message explaining the rejection? If so, what should the message say? | Tinayeshe & Tanaka |

## B. Testability Summary
*(Based on individual reviews)*
Tinayeshe and Tanaka noted that AC-1.2 fails testability because the form of the "no matching products" message is not stated. AC-2.2 fails because the maximum conflicts (10 vs 99) and no result is stated for exceeding it. AC-2.4 fails because "subtotal" could mean the line total for one product or the total of all products.
Tanya noted that AC-3.1 fails testability because "confirmation that the operation was successful" is ambiguous (pop-up? banner?).

## C. Coverage Summary
- **Story 1 (Product Search):** Good coverage. Includes expected path (AC-1.1), boundary (AC-1.3, AC-1.7), invalid case (AC-1.2), and interaction (AC-1.4).
- **Story 2 (Shopping Cart):** Expected path and invalid cases are covered, but boundary (AC-2.2) lacks a defined behaviour at the limit.
- **Story 3 (Favourites):** Good coverage of all paths.

## D. Test conditions
Tinayeshe and Tanaka noted that TC-2.2.2 uses a maximum of 99 while its source AC-2.2 says 10. Additionally, TC-3.4.2 requires "an appropriate message" but AC-3.4 only says the product must not appear twice. However, the team did well deriving conditions not explicitly stated in the ACs, such as TC-2.5.2 (other products stay in the cart) and TC-3.6.2 (removing one favourite keeps the others).

## E. Open questions
The section exists and states assumptions. However, Tinayeshe and Tanaka noted that Open question 1 assumes a maximum of 99, but AC-2.2 states 10, so the assumption was not carried into the criteria consistently. Open question 5 assumes a rejection message that AC-2.3 does not require. The entries also do not state which story or criterion they relate to.

## F. Decision

**Decision:** Accept with changes 

**Reasoning:** Team 07 has provided three user stories with acceptance criteria and related test conditions. Most criteria are understandable and testable, and the test basis covers expected user interactions. However, several issues need clarification before the test basis can be accepted without changes. These include ambiguous wording in the product search requirements, the contradiction between the maximum cart quantity of 10 in AC-2.2 and 99 in TC-2.2.2, missing behaviors for adding duplicate items to the cart, and assumptions in the open questions that are not yet confirmed. Some test conditions also need clearer wording (e.g., defining what an "appropriate" message is) to ensure they can be tested consistently.

## G. One thing done well

Team 07 has provided a good range of acceptance criteria covering both normal and exceptional user behaviour. For example, the product search story includes no-results handling, case-insensitive searches, category filtering, and empty searches. This gives testers several different scenarios to verify rather than focusing only on the successful search path.
