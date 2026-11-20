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
