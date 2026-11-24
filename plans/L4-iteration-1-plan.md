# Iteration 1 test plan — Team 06

**Build under test:** with-bugs · **Iteration:** 1 · **Dates:** 19 November 2026 to 20 November 2026
**Roles this iteration:** test lead Tanyaradzwa Mrewa · reporter Vimbainashe Chidhau · product owner Tanaka Zindi · scribe Tinayeshe Mugwagwa

## 1. Scope

What we will test in this iteration, by reference to the test conditions in `requirements/L3-test-basis.md`.

| We will test | Conditions | Why it is worth the time |
|---|---|---|
| Account Registration (Story 1) | TC-1.1.1 - TC-1.5.2 | Verifies successful registration, date validation, duplicate email handling, country/state selection and submission behaviour. |
| Product Information Management (Story 2) | TC-2.1.1 - TC-2.4.3 | Ensures product prices and stock quantities are saved correctly, invalid values are rejected and updates affect only the selected product. |
| Shopping Cart Management (Story 3) | TC-3.1.1 - TC-3.5.3 | Checks quantity updates, calculation of totals, invalid quantities, item removal and empty-cart behaviour. |

## 2. Out of scope

The section that decides whether this plan is real. Every exclusion carries a risk you are accepting — name it, or you have not excluded anything, only written a shorter list.

| We will not test | Risk we are accepting | Why we accept it |
|---|---|---|
| Performance and load testing | The application may bcome slow when many users access it simultaneously. | This iterationfocuses on functional correctness rather than system performance. |
| Security and penetration testing | Vulnerabilities such as unauthorized access or data xposure may remain undetected. | A dedicated security-testing activity is outside this iteration's scope. |
| External payment processing | Payment failures or transaction errors may not be detected. | Payment processing is not covered by the three user stories selected for this iteration. |

## 3. Approach

- **Test level(s):** System testing of complete user workflows and integration testing of interactions between application components and stored data.
- **Test types:** Functional, negative, boundary and regression testing.
- **Techniques we expect to use:** Boundary Value Analysis (e.g., search terms with 0 results vs 1 result; cart with 1 item vs max limit), Equivalence Partitioning (valid vs. invalid search terms), and Error Guessing.
- **What, if anything, we automate this iteration:** Nothing. We are executing manual tests first to stabilize the "with-bugs" build and verify our test conditions. Automation may be considered in a later iteration after the test cases and application behaviour are reviewed. 
## 4. Entry criteria

What must be true before we start executing.

- [ ] The `with-bugs` build is successfully deployed to the test environment and is accessible via the agreed URL.
- [ ] The test database is populated with basic user accounts and dummy product data (for search testing).
- [ ] All test conditions in `requirements/L3-test-basis.md` have been reviewed and approved by the team.
- [ ] The team can access the application and record test results and defects.

## 5. Exit criteria

What must be true before we stop. Agreed now, while nobody is under pressure.

- [ ] All planned test conditions (TC-1.x, TC-2.x, TC-3.x) have been executed at least once and their results logged in GitHub Issues.
- [ ] No open "Critical" or "High" severity defects remain in the Product Search or Checkout flows.
- [ ] At least 90% of all executed test cases pass.
- [ ] All defects found have been logged in GitHub Issues with clear reproduction steps and a screenshot showing the failure.



## 6. Risks to the testing itself

Not product risks — risks to our ability to test at all. Shared accounts changing under us, a team member unavailable, the environment going down.

| Risk | What we do if it happens |
|---|---|
| **Test Environment Downtime:** The staging server crashes or becomes unreachable. | Message the Dev team immediately. Pivot to reviewing test conditions or writing bug reports for previous findings while waiting. |
| **Team Member Unavailable:** A tester falls ill or has an emergency, leaving gaps in test execution. | The Test Lead will prioritize the remaining critical path tests (Search and Checkout) and skip low-priority UI tests until the member returns. |
| **Test Data Corruption:** Dummy user accounts or products get deleted/modified by other testers. | Keep a list of specific test accounts and product IDs in the test plan; if corrupted, we will re-seed the database or use newly created dummy accounts. |
