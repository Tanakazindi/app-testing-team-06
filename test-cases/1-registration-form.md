# Test cases — Registration Form

**Traces to:** `requirements/L3-test-basis.md`, Story 1
**Build:** with-bugs · **Author:** Tanyaradzwa Mrewa · **Reviewed by:** [Teammate Name]

---

## Identifier convention

| Prefix | What it is | Where it lives |
|---|---|---|
| `TC-x.y.z` | a **test condition** | `requirements/L3-test-basis.md` |
| `CS-nn` | a **test case** | this file |

Case identifiers are unique across the whole team. This form uses `CS-01` to `CS-15`.

---

## Partition analysis

| Field | Valid partitions | Invalid partitions | Ordered? | Boundaries (2-value) |
|---|---|---|---|---|
| Email | Correctly formed, not registered | Empty · Missing @ · Already registered | No | not applicable |
| Password | 8+ chars (Assumption Q3) | Empty · < 8 chars | length only | 7, 8 |
| Date of birth | YYYY-MM-DD, valid past date | Empty · Wrong format · Future date | yes | 2026-01-01, 2025-12-31 (assuming today is 2025) |
| Country | Poland (or supported list) | Empty | No | not applicable |
| State | Valid state for selected country | Empty · Duplicates country name | No | not applicable |

**Boundary strategy:** Two-value throughout. We test exactly at the minimum password length (8) and just below it (7). We test the current year's date and the previous year's date for the future-date rule.

---

## Cases

### CS-01 — Successful registration with valid data
- **Covers:** TC-1.1.1, TC-1.1.2
- **Type:** valid
- **Preconditions:** On the registration page. Email `newuser01@example.com` is not registered.
- **Data:** Email = `newuser01@example.com`, Password = `Password123!`, DOB = `1995-05-15`, Country = `Poland`, State = `Mazowieckie`, all other fields valid.
- **Steps:**
  1. Fill all fields with valid data.
  2. Click "Register" exactly once (Assumption Q1).
- **Expected result:** Account is created, and user is redirected to the "My account" page. (AC-1.1)

### CS-02 — Successful registration with exactly 8-character password
- **Covers:** TC-1.1.1
- **Type:** boundary
- **Preconditions:** On the registration page.
- **Data:** Password = `Abcdef1!` (exactly 8 chars), all else as CS-01 (new email).
- **Steps:**
  1. Fill all fields.
  2. Click "Register".
- **Expected result:** Account is created successfully. (AC-1.1, Assumption Q3)

### CS-03 — Password with 7 characters is rejected
- **Covers:** TC-1.1.1
- **Type:** boundary
- **Preconditions:** On the registration page.
- **Data:** Password = `Abcdef1` (7 chars), all else as CS-01 (new email).
- **Steps:**
  1. Fill all fields.
  2. Click "Register".
- **Expected result:** Registration rejected, error message about password length. (Assumption Q3)

### CS-04 — Valid Date of Birth is accepted
- **Covers:** TC-1.2.1
- **Type:** valid
- **Preconditions:** On the registration page.
- **Data:** DOB = `2000-01-01` (YYYY-MM-DD), all else valid.
- **Steps:**
  1. Fill all fields.
  2. Click "Register".
- **Expected result:** Account created successfully. (AC-1.2)

### CS-05 — Future Date of Birth is rejected
- **Covers:** TC-1.2.2
- **Type:** invalid
- **Preconditions:** On the registration page.
- **Data:** DOB = `2030-01-01` (Future year), all else valid.
- **Steps:**
  1. Fill all fields.
  2. Click "Register".
- **Expected result:** Registration rejected, error message about invalid date. (AC-1.2)

### CS-06 — Invalid Date format is rejected
- **Covers:** TC-1.2.2
- **Type:** invalid
- **Preconditions:** On the registration page.
- **Data:** DOB = `01/01/2000` (MM/DD/YYYY instead of YYYY-MM-DD), all else valid.
- **Steps:**
  1. Fill all fields.
  2. Click "Register".
- **Expected result:** Registration rejected, error message about date format. (AC-1.2)

### CS-07 — Email already in use is rejected
- **Covers:** TC-1.3.1, TC-1.3.2
- **Type:** invalid
- **Preconditions:** An account with `existing@example.com` already exists. On the registration page.
- **Data:** Email = `existing@example.com`, all else valid.
- **Steps:**
  1. Fill all fields.
  2. Click "Register".
- **Expected result:** Account not created. Error message "Email already in use" appears. (AC-1.3)

### CS-08 — State dropdown populates correctly for Poland
- **Covers:** TC-1.4.1
- **Type:** valid
- **Preconditions:** On the registration page.
- **Data:** Country = `Poland`, DOB = `1990-01-01`, all else valid.
- **Steps:**
  1. Select "Poland" from Country dropdown.
  2. Click the "State" dropdown.
- **Expected result:** The State dropdown shows states/regions within Poland (e.g., Mazowieckie), not a list of countries. (AC-1.4)

### CS-09 — State dropdown does not duplicate countries
- **Covers:** TC-1.4.2
- **Type:** invalid
- **Preconditions:** On the registration page.
- **Data:** Country = `Poland`
- **Steps:**
  1. Select "Poland" from Country dropdown.
  2. Click the "State" dropdown.
- **Expected result:** The list does not contain duplicates of the Country list (e.g., "Poland" or "Germany" do not appear). (AC-1.4)

### CS-10 — Single click submits form
- **Covers:** TC-1.5.1, TC-1.5.2
- **Type:** valid
- **Preconditions:** Form filled with valid data.
- **Steps:**
  1. Click the "Register" button exactly once.
  2. Do not click again.
- **Expected result:** The form submits immediately without requiring a second click. (AC-1.5, Assumption Q1)

### CS-11 — Empty Email is rejected
- **Covers:** TC-1.1.1
- **Type:** invalid
- **Preconditions:** On the registration page.
- **Data:** Email = `` (blank), all else valid.
- **Steps:**
  1. Leave email blank.
  2. Click "Register".
- **Expected result:** Registration rejected, error stating email is required. (AC-1.1)

### CS-12 — Empty Password is rejected
- **Covers:** TC-1.1.1
- **Type:** invalid
- **Preconditions:** On the registration page.
- **Data:** Password = `` (blank), all else valid.
- **Steps:**
  1. Leave password blank.
  2. Click "Register".
- **Expected result:** Registration rejected, error stating password is required. (AC-1.1)

---

## Coverage

| Condition from L3 | Covered by |
|---|---|
| TC-1.1.1 | CS-01, CS-02, CS-03, CS-11, CS-12 |
| TC-1.1.2 | CS-01 |
| TC-1.2.1 | CS-04 |
| TC-1.2.2 | CS-05, CS-06 |
| TC-1.3.1 | CS-07 |
| TC-1.3.2 | CS-07 |
| TC-1.4.1 | CS-08 |
| TC-1.4.2 | CS-09 |
| TC-1.5.1 | CS-10 |
| TC-1.5.2 | CS-10 |
