# Test cases — Shopping Cart Quantity

**Traces to:** `requirements/L3-test-basis.md`, Story 3
**Build:** with-bugs · **Author:** Tanyaradzwa Mrewa · **Reviewed by:** [Teammate Name]

---

## Identifier convention

This form uses `CS-40` to `CS-53`.

---

## Partition analysis

| Field | Valid partitions | Invalid partitions | Ordered? | Boundaries (2-value) |
|---|---|---|---|---|
| Quantity | Whole number >= 1 | Zero · Negative · Fractional · Blank | Yes | 0, 1 |

**Boundary strategy:** Two-value on the lower bound. The minimum accepted quantity is 1, so we test 1 (valid) and 0 (invalid). Since no maximum quantity is defined in the requirements (Assumption Q10), we only test the lower boundary.

---

## Cases

### CS-40 — Change quantity to valid positive number
- **Covers:** TC-3.1.1
- **Type:** valid
- **Preconditions:** Cart contains 1 unit of "Claw Hammer" (Price $10). User is on the cart page.
- **Data:** Quantity = `2`
- **Steps:**
  1. Change quantity from 1 to 2.
  2. Click update/save.
- **Expected result:** Cart displays the new quantity (2). (AC-3.1)

### CS-41 — Line total recalculated correctly
- **Covers:** TC-3.1.2
- **Type:** valid
- **Preconditions:** Same as CS-40. Unit price is $10.
- **Data:** Quantity = `3`
- **Steps:**
  1. Change quantity to 3.
  2. Click update.
- **Expected result:** Item's line total equals $30 (Unit price $10 x quantity 3). (AC-3.1)

### CS-42 — Cart total recalculated correctly
- **Covers:** TC-3.1.3
- **Type:** valid
- **Preconditions:** Cart contains Item A ($10) and Item B ($20). Change Item A quantity to 2.
- **Data:** Quantity of Item A = `2`
- **Steps:**
  1. Update Item A quantity to 2.
- **Expected result:** Cart total equals $40 ($20 for Item A + $20 for Item B). (AC-3.1)

### CS-43 — Changing one product leaves others unchanged
- **Covers:** TC-3.1.4
- **Type:** valid
- **Preconditions:** Cart contains Item A and Item B.
- **Data:** Quantity of Item A = `4`
- **Steps:**
  1. Update Item A quantity to 4.
- **Expected result:** Item B's quantity and line total remain unchanged. (AC-3.1)

### CS-44 — Minimum accepted quantity (1) is accepted
- **Covers:** TC-3.2.1
- **Type:** boundary
- **Preconditions:** Cart contains 1 item.
- **Data:** Quantity = `1`
- **Steps:**
  1. Ensure quantity is set to 1.
  2. Click update.
- **Expected result:** Quantity 1 is accepted and saved. (AC-3.2)

### CS-45 — Totals correct at quantity 1
- **Covers:** TC-3.2.2
- **Type:** boundary
- **Preconditions:** Unit price $10.
- **Data:** Quantity = `1`
- **Steps:**
  1. Update to 1.
- **Expected result:** Line total is $10, cart total matches. (AC-3.2)

### CS-46 — Value immediately below minimum (0) is not accepted
- **Covers:** TC-3.2.3
- **Type:** boundary
- **Preconditions:** Cart contains 1 item.
- **Data:** Quantity = `0`
- **Steps:**
  1. Enter 0.
  2. Click update.
- **Expected result:** Change is rejected (does not save as 0). (AC-3.2, Assumption Q9)

### CS-47 — Quantity zero is rejected
- **Covers:** TC-3.3.1
- **Type:** invalid
- **Preconditions:** Cart contains 1 item.
- **Data:** Quantity = `0`
- **Steps:**
  1. Enter 0.
  2. Click update.
- **Expected result:** Change rejected. Message says positive whole number required. Quantity remains 1. (AC-3.3, Assumption Q9)

### CS-48 — Negative quantity is rejected
- **Covers:** TC-3.3.2
- **Type:** invalid
- **Preconditions:** Cart contains 1 item.
- **Data:** Quantity = `-5`
- **Steps:**
  1. Enter -5.
  2. Click update.
- **Expected result:** Change rejected. Message explains positive whole number required. (AC-3.3)

### CS-49 — Fractional quantity is rejected
- **Covers:** TC-3.3.3
- **Type:** invalid
- **Preconditions:** Cart contains 1 item.
- **Data:** Quantity = `1.5`
- **Steps:**
  1. Enter 1.5.
  2. Click update.
- **Expected result:** Change rejected. Message explains positive whole number required. (AC-3.3)

### CS-50 — Blank quantity is rejected
- **Covers:** TC-3.3.4
- **Type:** invalid
- **Preconditions:** Cart contains 1 item.
- **Data:** Quantity = `` (blank)
- **Steps:**
  1. Delete the number in the quantity box.
  2. Click update.
- **Expected result:** Change rejected. Message explains positive whole number required. (AC-3.3)

### CS-51 — Rejection message is specific
- **Covers:** TC-3.3.5
- **Type:** invalid
- **Preconditions:** Cart contains 1 item.
- **Data:** Quantity = `0`
- **Steps:**
  1. Enter 0.
  2. Click update.
- **Expected result:** The rejection message explicitly states that a positive whole number is required. (AC-3.3)

### CS-52 — Saved quantity unchanged after rejection
- **Covers:** TC-3.3.6
- **Type:** invalid
- **Preconditions:** Cart contains 2 items. User attempts to change to 0.
- **Data:** Quantity = `0`
- **Steps:**
  1. Enter 0.
  2. Click update.
  3. Refresh page.
- **Expected result:** The quantity remains at 2 (the previously saved valid amount). (AC-3.3)

### CS-53 — Totals unchanged after rejection
- **Covers:** TC-3.3.7
- **Type:** invalid
- **Preconditions:** Cart contains 2 items at $10 each.
- **Data:** Quantity = `-1`
- **Steps:**
  1. Enter -1.
  2. Click update.
- **Expected result:** Line total remains $20, cart total remains $20. (AC-3.3)

---

## Coverage

| Condition from L3 | Covered by |
|---|---|
| TC-3.1.1 | CS-40 |
| TC-3.1.2 | CS-41 |
| TC-3.1.3 | CS-42 |
| TC-3.1.4 | CS-43 |
| TC-3.2.1 | CS-44 |
| TC-3.2.2 | CS-45 |
| TC-3.2.3 | CS-46 |
| TC-3.3.1 | CS-47 |
| TC-3.3.2 | CS-48 |
| TC-3.3.3 | CS-49 |
| TC-3.3.4 | CS-50 |
| TC-3.3.5 | CS-51 |
| TC-3.3.6 | CS-52 |
| TC-3.3.7 | CS-53 |
