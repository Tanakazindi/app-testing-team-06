
# Session L1 — Team 06

Date: [14/10/2026]
Build under test: Toolshop — with-bugs
URL: https://with-bugs.practicesoftwaretesting.com/
Participants: Tanaka Zindi, Tanyaradzwa Mrewa, Tinayeshe Mugwagwa, Vimbainashe Aulyn Chidhau
Time box: 40 minutes

## Charters

- Tanaka Zindi: Explore the cart and checkout with different product quantities, item removals, and valid and invalid billing and payment inputs to discover problems with totals, validation and completing an order.
- Tanyaradzwa Mrewa: Explore [area] with [resources or test data] to discover [information sought].
- Tinayeshe Mugwagwa: Explore [area] with [resources or test data] to discover [information sought].
- Vimbainashe Aulyn Chidhau: Explore [area] with [resources or test data] to discover [information sought].

## Product model (from step 1)

- Visitor can: Browse products, open product details, add products to cart, adjust the price range, sort alphabetically or by CO2 rating, filter by category, sustainability and brand, and access the contact page and bug hunting guide.
- Logged-in customer can: Access their account to manage their profile, favourites and orders, and access messages and invoices.
- Administrator can: View sales charts and recent orders, inspect order information and update order statuses.
- Where money appears: Product prices appear in the homepage catalogue and on individual product pages. The cart displays item prices, item totals and the overall total. The team also identified an invoices section in the customer account.
- What this product is for: An online shop where customers, including people who use tools for work or home projects, can browse and buy tools.

## Session log

| # | Mark | Area | What happened | How to get back to it |
|---|------|------|---------------|-----------------------|
| 1 | ANOMALY | Cart & checkout | Tanaka Zindi: Item line totals remain $00.00, including after changing quantities. The unit price displays correctly. For example, 3 Combination Pliers at $14.15 each should have a line total of $42.45. Observed both while logged out and while logged in as a customer. | Open Combination Pliers, add it to the cart, open the cart and change its quantity to 3. Observe the item's Total column. Repeat while logged out and while logged in. |
| 2 | ANOMALY | Cart & checkout | Tanaka Zindi: Clicking the X button beside an item does not remove it from the cart. Observed both while logged out and while logged in as a customer. | Add Combination Pliers to the cart, open the cart and click the X beside the item. Observe that the item remains. Repeat while logged out and while logged in. |
| 3 | NOTE | Cart & checkout | Tanaka Zindi: The overall cart total correctly accounts for product prices and quantities, despite the individual item totals displaying $00.00. | Add products to the cart, change their quantities and compare the overall cart total with the sum of each unit price multiplied by its quantity. |
| 4 | ANOMALY | Cart & checkout | Tanaka Zindi: While logged in, attempting to add another Combination Pliers with quantity 1 displayed “Oops, something went wrong.” The additional item was not added. | While logged in with Combination Pliers already in the cart, go to Categories → Hand Tools, filter for Pliers, open Combination Pliers and click Add to cart with quantity 1. Observe the error and inspect the cart. |
| 5 | ANOMALY | Cart & checkout | Tanaka Zindi: While logged in, attempting to add Combination Pliers again reset existing cart quantities to 1 and reduced the overall total. In a follow-up, quantity 2 survived a refresh but reset to 1 after another add attempt from the homepage. | While logged in, set the cart quantity for Combination Pliers to 2, click outside the field and refresh. Confirm it remains 2. From the homepage, open Combination Pliers and attempt to add it again. Return to the cart and inspect the quantity. |
| 6 | QUESTION | Cart & checkout | Tanaka Zindi: Entering 0, clearing the quantity field or entering 1.5 produces no apparent change to the cart calculation. It is unclear how the cart handles these inputs. | In the cart, try 0, a blank value and 1.5 in a quantity field. Record whether each value remains visible, whether a validation message appears and whether the overall total changes. |
| 7 | NOTE | Cart & checkout | Tanaka Zindi: Refreshing the page after entering quantity 0 restores the previous quantity. | Change a cart quantity to 0, then refresh the page and inspect the quantity field. |
| 8 | NOTE | Cart & checkout | Tanaka Zindi: A valid cart quantity of 2 remained saved after clicking outside the field and refreshing the page while logged in. | Set Combination Pliers quantity to 2 in the cart, click outside the field, refresh and inspect the quantity. |
| 9 | ANOMALY | Checkout — Address | Tanaka Zindi: The green button at the bottom right of the Billing Address step has no visible text, leaving its purpose unclear. | Proceed through checkout to the Address step. Inspect the green button beneath the billing address fields. |
| 10 | ANOMALY | Checkout — Payment | Tanaka Zindi: Bank transfer reaches an order confirmation displaying an invoice number. Cash on delivery, credit card, buy now pay later, gift card and the option labelled “error 304 missing payment gateway” display a payment-success message but remain on the payment form without showing that order confirmation. | Reach the Payment step, select a payment method, complete the displayed fields as needed and click Confirm. Compare the outcome for each listed method with the bank-transfer outcome. The notes do not establish whether every method was tested through a fresh checkout. |
| 11 | ANOMALY | Checkout — Payment | Tanaka Zindi: Selecting Cash on Delivery displays bank-name and account-number fields that appear unrelated to paying on delivery. Whether these fields are mandatory was not established. | Proceed to the Payment step, select Cash on Delivery and inspect the bank-name and account-number fields beneath the dropdown. |


[Add each member's actual observations using ANOMALY, QUESTION, NOTE or BLOCKED. Identify the observer in each entry.]

## Debrief

1. Covered / not covered: [List the areas actually explored and the areas nobody tested.]
2. What we found: [Summarise the findings and explain whether any appear serious.]
3. What got in the way: [Describe actual blockers or uncertainties. If none occurred, say so.]
4. What we learned: [Explain what the team learned about the product.]
5. Next charter should be: [Suggest the next exploration based on findings or gaps.]
