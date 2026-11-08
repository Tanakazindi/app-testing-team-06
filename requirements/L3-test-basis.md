# Test basis L3 — Team 06

Build under test: with-bugs  
Date: 03 November 2026  
Authors: Tanyaradzwa Mrewa (Story 1), Vimbainashe Chidhau (Story 2), Tanaka Zindi and Tinayeshe Mugwagwa(Story 3)

---

## Story 1 — Registering an account

**As a** new customer **I want** to create an account with my personal details **so that** I can check out faster and view my order history without re-entering my data.

### Acceptance criteria

- AC-1.1 (scenario) Given a new user on the registration page, when they fill in all required fields with valid data and click "Register", then the account is created and they are redirected to the "My account" page.
- AC-1.2 (rule, boundary) The Date of birth field must accept a valid date in YYYY-MM-DD format, and the system must reject dates in the future.
- AC-1.3 (scenario, invalid case) Given an E-mail address that is already registered in the system, when the user attempts to register, then the account is not created and an error message stating "Email already in use" appears.
- AC-1.4 (scenario, interaction with another rule) Given the user has selected "Poland" as their Country, when they open the "State" dropdown, then the options displayed should be states/regions within Poland, not a duplicate list of countries.
- AC-1.5 (scenario, invalid case) Given the registration form is fully filled out, when the user clicks the "Register" button exactly once, then the form submits immediately without requiring a second click.

### Test conditions

| ID | Condition | From |
|----|-----------|------|
| TC-1.1.1 | A complete, valid form creates a new account | AC-1.1 |
| TC-1.1.2 | User is redirected to the "My account" page after successful registration | AC-1.1 |
| TC-1.2.1 | A valid Date of birth in YYYY-MM-DD format is accepted | AC-1.2 |
| TC-1.2.2 | A future date (e.g., year 203) is rejected | AC-1.2 |
| TC-1.3.1 | Registration is rejected if the email is already in use | AC-1.3 |
| TC-1.3.2 | An error message explains the duplicate email issue | AC-1.3 |
| TC-1.4.1 | The "State" dropdown is populated correctly based on the selected Country | AC-1.4 |
| TC-1.4.2 | The "State" dropdown does not duplicate the Country list | AC-1.4 |
| TC-1.5.1 | A single click on the "Register" button submits the form | AC-1.5 |
| TC-1.5.2 | The system does not require a second click to process registration | AC-1.5 |

---

## Story 2 — [Short name]

**As an administrator, I want to create and update product information, including prices and stock quantities, so that customers can see accurate product details and availability.** 

### Acceptance criteria

AC-2.1 — Expected path (scenario)

Given an administrator is editing an existing product with valid product information, when they save the changes, then the system saves the updated price and stock quantity and displays a confirmation message.

AC-2.2 — Boundary (rule)

A product's stock quantity must not be lower than zero. A stock quantity of zero represents an out-of-stock product.

AC-2.3 — Invalid case (scenario)

Given an administrator is editing a product, when they enter a negative stock quantity or a negative price and attempt to save, then the system rejects the invalid value and displays a validation message.

AC-2.4 — Interaction (scenario)

Given an administrator is updating the price and stock quantity of one product, when the changes are saved, then the updated values belong only to that product and the information of other products remains unchanged.

### Test conditions


|ID	|Test condition	|From
|----|-----------|-----|
|TC-2.1.1	|Saving valid changes to an existing product's price and stock quantity|	AC-2.1|
|TC-2.1.2|	Confirmation message after successfully saving product changes|	AC-2.1|
|TC-2.2.1|	Acceptance of zero as a stock quantity |	AC-2.2|
|TC-2.2.2|	Rejection of stock quantities below zero |	AC-2.2|
|TC-2.3.1|	Validation of negative product prices |	AC-2.3|
|TC-2.3.2|	Validation of negative stock quantities |	AC-2.3|
|TC-2.3.3	|Display of validation feedback when invalid product values are submitted	|AC-2.3|
|TC-2.4.1|	Correct association of updated prices with the selected product|	AC-2.4|
|TC-2.4.2|	Correct association of updated stock quantities with the selected product	|AC-2.4|
|TC-2.4.3|	Preservation of other products' information after an update|	AC-2.4|

---

## Story 3 — [Managing the shopping cart]

**As a customer I want to change product quantities and remove products from my cart so that I can review the cost and buy only the products and quantities I need.** 

### Acceptance criteria

- AC-3.1 (scenario, expected path) Given a cart containing a product, when the customer changes its quantity to a valid positive whole number, then the cart displays the new quantity, the item's line total equals its unit price multiplied by its quantity, and the cart total equals the sum of all item line totals.

- AC-3.2 (rule, boundary) The minimum accepted quantity for a product remaining in the cart is 1. A quantity of 1 must be accepted.

- AC-3.3 (scenario, invalid case) Given a cart containing a product, when the customer submits a quantity of zero, a negative number, a fractional number or a blank value, then the change is rejected, a message explains that a positive whole number is required, and the previously saved quantity and totals remain unchanged.

- AC-3.4 (scenario, removal) Given a cart containing a product, when the customer selects its remove button, then that product's row disappears, the remaining products retain their quantities, and the cart total equals the sum of the remaining item line totals.

- AC-3.5 (scenario, interaction with checkout) Given a cart containing only one product, when the customer removes that product, then the cart displays an empty-cart message and a total of zero, and checkout cannot proceed.

### Test conditions

| ID | Condition | From |
|----|-----------|------|
| TC-3.1.1 | | AC-3.1 |
| TC-3.1.2 | | AC-3.1 |

---

## Open questions

| # | Question | What we assumed | Why it matters |
|---|----------|-----------------|----------------|
| 1 | Why does the "Register" button sometimes require a second click to process? | This is a UI bug. It should work on the first click. | Affects AC-1.5 and TC-1.5.1/2. If it's a deliberate feature, we need to know why. |
| 2 | Should the "State" dropdown show states or countries when a country is selected? | It should show states/provinces within the selected country. | Affects AC-1.4. If the app is only meant to support Country-level, the field should be removed or renamed. |
| 3 | What are the password complexity rules? | We assume at least 8 characters. | The form doesn't state the rule. If we don't know it, we can't test invalid passwords (AC-1.1). |
| 4 | What is the maximum length for the Address field? | We assume 255 characters. | The address field text overflows in the UI. We need to know if there's a character limit. |
| 5 | Should a product be allowed to have a stock quantity of zero? | Zero is allowed and represents an out-of-stock product. | Determines whether zero should be accepted or rejected during validation. |
| 6 | Should a product price be allowed to equal zero? | A product must have a positive price. | Determines the minimun acceptable price. |
| 7 | Should administrators be allowed to enter decimal values for stock quantities? | We assume stock quantities should be whole numbers. | Prevents invalid fractional stock values. |
| 8 | Should updating one product ever affect the values of another product? | Each product should be updated independently. | Protects the accuracy of product records. |
| 9 | Should entering quantity zero remove the product or reject the change? | Zero is rejected with a validation message, preserving the previous quantity and totals. | Determines the expected behaviour in AC-3.2 and AC-3.3 and prevents zero-unit orders. |



