# Iteration 1 test plan — Team 06

**Build under test:** with-bugs · **Iteration:** 1 · **Dates:** 19 November 2026 to 20 November 2026
**Roles this iteration:** test lead Tanyaradzwa Mrewa · reporter Vimbainashe Chidhau · product owner Tanaka Zindi · scribe Tinayeshe Mugwagwa

## 1. Scope

What we will test in this iteration, by reference to the test conditions in `requirements/L3-test-basis.md`.

| We will test | Conditions | Why it is worth the time |
|---|---|---|
| Product Search (Story 1) | TC-1.1.1, TC-1.2.1, TC-1.3.1, TC-1.4.1 | Core user journey; if users cannot find products, the site is unusable. |
| Shopping Cart Limits (Story 2) | TC-2.1.1, TC-2.2.1, TC-2.2.2, TC-2.3.1 | High risk of bugs (e.g., the contradiction between max 10 vs 99 items). Essential for revenue. |
| Checkout Flow (Story 3) | TC-3.1.1, TC-3.2.1, TC-3.3.1 | The final and most critical step. Bugs here result in lost sales and abandoned carts. |

## 2. Out of scope

The section that decides whether this plan is real. Every exclusion carries a risk you are accepting — name it, or you have not excluded anything, only written a shorter list.

| We will not test | Risk we are accepting | Why we accept it |
|---|---|---|
| Admin Panel & Inventory Management | An administrator could accidentally delete a product or misprice it, and we wouldn't catch it before release. | No customer reaches this interface directly. Our limited time is better spent ensuring the customer search and cart flow is flawless. |
| Cross-browser compatibility (IE11, Safari) | Users on older browsers or Safari may experience UI glitches (e.g., misaligned search bars or broken layouts). | Analytics show 95% of our target demographic uses Chrome/Edge. We accept the minor UI risk to test core logic on our primary platform. |
| Password reset via email | Users who forget their password may be locked out permanently if the email server fails. | This is a lower-frequency action. We will test the login itself, and accept the risk that the reset flow may have minor bugs until Iteration 2. |

## 3. Approach

- **Test level(s):** System Testing (end-to-end flows) and Integration Testing (App to Database).
- **Test types:** Functional testing (black-box) and basic UI/UX validation (visual checks).
- **Techniques we expect to use:** Boundary Value Analysis (e.g., search terms with 0 results vs 1 result; cart with 1 item vs max limit), Equivalence Partitioning (valid vs. invalid search terms), and Error Guessing.
- **What, if anything, we automate this iteration:** Nothing. We are executing manual tests first to stabilize the "with-bugs" build and verify our test conditions before writing any automation scripts.

## 4. Entry criteria

What must be true before we start executing.

- [ ] The `with-bugs` build is successfully deployed to the test environment and is accessible via the agreed URL.
- [ ] The test database is populated with basic user accounts and dummy product data (for search testing).
- [ ] All test conditions in `requirements/L3-test-basis.md` have been reviewed and approved by the team.

## 5. Exit criteria

What must be true before we stop. Agreed now, while nobody is under pressure.

- [ ] All planned test conditions (TC-1.x, TC-2.x, TC-3.x) have been executed at least once and their results logged in GitHub Issues.
- [ ] No open "Critical" or "High" severity defects remain in the Product Search or Checkout flows.
- [ ] At least 90% of all executed test cases pass.
- [ ] All defects found have been logged in GitHub Issues with clear reproduction steps and a screenshot showing the failure.

*Sanity check: if these could be met on the first day they are too weak; if they could never be met the plan is fiction.*

## 6. Risks to the testing itself

Not product risks — risks to our ability to test at all. Shared accounts changing under us, a team member unavailable, the environment going down.

| Risk | What we do if it happens |
|---|---|
| **Test Environment Downtime:** The staging server crashes or becomes unreachable. | Message the Dev team immediately. Pivot to reviewing test conditions or writing bug reports for previous findings while waiting. |
| **Team Member Unavailable:** A tester falls ill or has an emergency, leaving gaps in test execution. | The Test Lead will prioritize the remaining critical path tests (Search and Checkout) and skip low-priority UI tests until the member returns. |
| **Test Data Corruption:** Dummy user accounts or products get deleted/modified by other testers. | Keep a list of specific test accounts and product IDs in the test plan; if corrupted, we will re-seed the database or use newly created dummy accounts. |
