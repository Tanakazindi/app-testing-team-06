# Test basis L3 — Team 06

Build under test: with-bugs  
Date: 03 November 2026  
Authors: Tanya Mrewa (Story 1), Vimbainashe Chidau (Story 2), Tanaka Zindi (Story 3)

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

**As a** ... **I want** ... **so that** ...

### Acceptance criteria

- AC-2.1 (scenario) ...
- AC-2.2 (rule, boundary) ...
- AC-2.3 (scenario, invalid case) ...
- AC-2.4 (rule, interaction) ...

### Test conditions

| ID | Condition | From |
|----|-----------|------|
| TC-2.1.1 | | AC-2.1 |
| TC-2.1.2 | | AC-2.1 |

---

## Story 3 — [Short name]

**As a** ... **I want** ... **so that** ...

### Acceptance criteria

- AC-3.1 (scenario) ...
- AC-3.2 (rule, boundary) ...
- AC-3.3 (scenario, invalid case) ...
- AC-3.4 (rule, interaction) ...

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
