# Test Cases — Shopping Cart Management

**Traces to:** `requirements/L3-test-basis.md`, Story 3  
**Build:** with-bugs  
**Authors:** Tanaka Zindi and Tinayeshe Mugwagwa  
**Reviewed by:** To be assigned

---

## Partition Analysis

The partition analysis focuses on shopping cart quantity management, based on acceptance criteria AC-3.1, AC-3.2 and AC-3.3.

| Field | Valid partitions | Invalid partitions | Ordered? | Boundaries (2-value) |
|---|---|---|---|---|
| Product quantity | Positive whole numbers (1, 2, 3, etc.) | Zero (0), negative numbers (-1, -2), fractional numbers (1.5, 2.5), blank input | Yes | 0, 1 |
 
### Boundary Strategy

We use **two-value boundary analysis** because our acceptance criteria define a minimum valid quantity of 1.

The two boundary values are:

- **0:** Immediately below the minimum accepted quantity; expected to be rejected.
- **1:** Minimum valid quantity; expected to be accepted.

No maximum quantity is specified in our Laboratory 3 test basis, so we do not assume an upper boundary.

### Equivalence Partitions

The quantity input is divided into the following equivalence classes:

| Partition | Example input | Expected behaviour | Related test condition |
|---|---|---|---|
| Valid positive whole number | 2 | Quantity is accepted and cart totals are recalculated. | TC-3.1.1, TC-3.1.2, TC-3.1.3 |
| Minimum valid quantity | 1 | Quantity is accepted. | TC-3.2.1 |
| Zero quantity | 0 | Change is rejected; previous quantity and totals remain unchanged. | TC-3.3.1 |
| Negative quantity | -1 | Change is rejected; previous quantity and totals remain unchanged. | TC-3.3.2 |
| Fractional quantity | 1.5 | Change is rejected; previous quantity and totals remain unchanged. | TC-3.3.3 |
| Blank quantity | Empty field | Change is rejected; previous quantity and totals remain unchanged. | TC-3.3.4 |

### Additional Functionality Covered by Story 3

Although the following are not separate form input fields, the corresponding behaviour will be considered when deriving test cases:

**Product removal (AC-3.4):**
- Removing a product should remove its row from the cart.
- Other products should retain their quantities.
- The cart total should be recalculated.

**Empty cart and checkout (AC-3.5):**
- Removing the last product should display an empty-cart message.
- The cart total should become zero.
- Checkout should not proceed when the cart is empty.

These behaviours will be tested separately from the input partition analysis.


## Cases

### CS-40 — Valid quantity change updates cart totals

- **Covers:** TC-3.1.1, TC-3.1.2, TC-3.1.3
- **Type:** Valid
- **Preconditions:** Open the Toolshop `with-bugs` application. Add one Combination Pliers product to the shopping cart. Confirm its initial quantity is 1 and record its displayed unit price.
- **Data:** Product = Combination Pliers; new quantity = 2.
- **Steps:**
  1. Open the shopping cart.
  2. Locate Combination Pliers.
  3. Change the quantity from 1 to 2.
  4. Apply the quantity change.
  5. Observe the displayed quantity, item line total, and overall cart total.
- **Expected result:** The cart displays quantity 2. The item's line total equals the unit price multiplied by 2. Since the cart contains only one product, the overall cart total equals that line total (AC-3.1).

### CS-41 — Minimum valid quantity is accepted

- **Covers:** TC-3.2.1, TC-3.2.2
- **Type:** Boundary
- **Preconditions:** Combination Pliers is present in the shopping cart with quantity 2.
- **Data:** New quantity = 1.
- **Steps:**
  1. Open the shopping cart.
  2. Change the quantity of Combination Pliers from 2 to 1.
  3. Apply the change.
  4. Observe the quantity and totals.
- **Expected result:** Quantity 1 is accepted. The item line total equals its unit price, and the overall cart total reflects the updated quantity (AC-3.1, AC-3.2).

### CS-42 — Zero quantity is rejected

- **Covers:** TC-3.2.3, TC-3.3.1, TC-3.3.5, TC-3.3.6, TC-3.3.7
- **Type:** Boundary
- **Preconditions:** Combination Pliers is present in the shopping cart with a previously saved quantity of 2.
- **Data:** New quantity = 0.
- **Steps:**
  1. Open the shopping cart.
  2. Change the product quantity from 2 to 0.
  3. Apply the change.
  4. Observe the displayed quantity, validation message, and totals.
- **Expected result:** The system rejects quantity 0 and displays a message explaining that a positive whole number is required. The previously saved quantity remains 2, and the line total and cart total remain unchanged (AC-3.2, AC-3.3).

### CS-43 — Negative quantity is rejected

- **Covers:** TC-3.3.2, TC-3.3.5, TC-3.3.6, TC-3.3.7
- **Type:** Invalid
- **Preconditions:** Combination Pliers is present in the shopping cart with a previously saved quantity of 2.
- **Data:** New quantity = -1.
- **Steps:**
  1. Open the shopping cart.
  2. Enter -1 in the quantity field.
  3. Apply the change.
  4. Observe the validation message, quantity, and totals.
- **Expected result:** The negative quantity is rejected. A message explains that a positive whole number is required. The previously saved quantity of 2 and the cart totals remain unchanged (AC-3.3).

### CS-44 — Fractional quantity is rejected

- **Covers:** TC-3.3.3, TC-3.3.5, TC-3.3.6, TC-3.3.7
- **Type:** Invalid
- **Preconditions:** Combination Pliers is present in the shopping cart with a previously saved quantity of 2.
- **Data:** New quantity = 1.5.
- **Steps:**
  1. Open the shopping cart.
  2. Enter 1.5 in the quantity field.
  3. Apply the change.
  4. Observe the validation message and cart values.
- **Expected result:** The fractional quantity is rejected because quantities must be positive whole numbers. A validation message is displayed, and the previously saved quantity and totals remain unchanged (AC-3.3).

### CS-45 — Empty quantity field is rejected

- **Covers:** TC-3.3.4, TC-3.3.5, TC-3.3.6, TC-3.3.7
- **Type:** Invalid
- **Preconditions:** Combination Pliers is present in the shopping cart with a previously saved quantity of 2.
- **Data:** Quantity = blank (empty string).
- **Steps:**
  1. Open the shopping cart.
  2. Select the quantity field.
  3. Delete the existing value, leaving the field completely empty.
  4. Apply the change.
  5. Observe the validation message and cart totals.
- **Expected result:** The blank quantity is rejected. A message explains that a positive whole number is required. The previously saved quantity of 2 and the cart totals remain unchanged (AC-3.3).

### CS-46 — Changing one product does not affect another product

- **Covers:** TC-3.1.1, TC-3.1.2, TC-3.1.3, TC-3.1.4
- **Type:** Valid
- **Preconditions:** The shopping cart contains Combination Pliers and Claw Hammer, each with quantity 1. Record both unit prices.
- **Data:** Combination Pliers quantity = 3; Claw Hammer quantity = 1.
- **Steps:**
  1. Open the shopping cart containing both products.
  2. Change Combination Pliers quantity from 1 to 3.
  3. Apply the change.
  4. Observe the quantities and line totals of both products.
  5. Check the overall cart total.
- **Expected result:** Combination Pliers displays quantity 3, and its line total equals its unit price multiplied by 3. Claw Hammer remains at quantity 1 with its original line total. The overall cart total equals the sum of both line totals (AC-3.1).

### CS-47 — Removing one product preserves other cart items

- **Covers:** TC-3.4.1, TC-3.4.2, TC-3.4.3
- **Type:** Valid
- **Preconditions:** The shopping cart contains Combination Pliers at quantity 2 and Claw Hammer at quantity 1. Record their unit prices and the initial cart total.
- **Data:** Product to remove = Combination Pliers.
- **Steps:**
  1. Open the shopping cart.
  2. Locate Combination Pliers.
  3. Click its remove (X) button.
  4. Observe the remaining cart contents.
  5. Check the updated cart total.
- **Expected result:** Combination Pliers is completely removed. Claw Hammer remains in the cart with quantity 1. The cart total equals the line total of the remaining Claw Hammer product (AC-3.4).

### CS-48 — Removing the last product results in an empty cart

- **Covers:** TC-3.4.1, TC-3.4.3, TC-3.5.1, TC-3.5.2
- **Type:** Valid
- **Preconditions:** The shopping cart contains only Combination Pliers at quantity 1.
- **Data:** Product to remove = Combination Pliers.
- **Steps:**
  1. Open the shopping cart.
  2. Locate Combination Pliers.
  3. Click its remove (X) button.
  4. Observe the shopping cart contents and total.
- **Expected result:** Combination Pliers is removed. The shopping cart displays an empty-cart message and a total of zero (AC-3.4, AC-3.5).

### CS-49 — Checkout cannot proceed with an empty cart

- **Covers:** TC-3.5.3
- **Type:** Invalid
- **Preconditions:** The shopping cart contains no products.
- **Data:** Cart item count = 0; cart total = 0.
- **Steps:**
  1. Open the empty shopping cart.
  2. Locate the checkout or proceed-to-checkout control, if displayed.
  3. Attempt to proceed to checkout using any available control.
  4. Observe whether the checkout process begins.
- **Expected result:** Checkout cannot proceed while the cart is empty. The customer must not advance into the checkout process (AC-3.5).

---

## Coverage

| Condition from L3 | Covered by |
|---|---|
| TC-3.1.1 | CS-40, CS-46 |
| TC-3.1.2 | CS-40, CS-46 |
| TC-3.1.3 | CS-40, CS-46 |
| TC-3.1.4 | CS-46 |
| TC-3.2.1 | CS-41 |
| TC-3.2.2 | CS-41 |
| TC-3.2.3 | CS-42 |
| TC-3.3.1 | CS-42 |
| TC-3.3.2 | CS-43 |
| TC-3.3.3 | CS-44 |
| TC-3.3.4 | CS-45 |
| TC-3.3.5 | CS-42, CS-43, CS-44, CS-45 |
| TC-3.3.6 | CS-42, CS-43, CS-44, CS-45 |
| TC-3.3.7 | CS-42, CS-43, CS-44, CS-45 |
| TC-3.4.1 | CS-47, CS-48 |
| TC-3.4.2 | CS-47 |
| TC-3.4.3 | CS-47, CS-48 |
| TC-3.5.1 | CS-48 |
| TC-3.5.2 | CS-48 |
| TC-3.5.3 | CS-49 |

**Coverage summary:** All 20 test conditions from Story 3 are covered by the 10 test cases.

**Boundary strategy:** Two-value boundary analysis is applied to the minimum valid quantity, using values 0 and 1. No upper boundary is tested because the test basis does not define a maximum quantity.
