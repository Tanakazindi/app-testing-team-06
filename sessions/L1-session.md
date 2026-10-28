# Session L1 — Team 06

Date: 14/10/2026
Build under test: Toolshop — with-bugs
URL: https://with-bugs.practicesoftwaretesting.com/
Participants: Tanaka Zindi, Tanyaradzwa Mrewa, Tinayeshe Mugwagwa, Vimbainashe Aulyn Chidhau
Time box: 40 minutes

## Charters

- Tanaka Zindi: Explore the cart and checkout with different product quantities, item removals, and valid and invalid billing and payment inputs to discover problems with totals, validation and completing an order.
- Tanyaradzwa Mrewa: Explore the product filtering system (price range, sorting by name/price/CO₂ rating, category, brand and sustainability filters) with extreme values, empty selections, contradictory combinations and rapid filter changes to discover filter logic, input-handling and result-correctness problems.
- Tinayeshe Mugwagwa: Explore registration, login and the customer account pages (profile, favourites, invoices, messages) with invalid sign-up data, edited profile details and a second browser session open to discover validation, data-saving and session problems.
- Vimbainashe Aulyn Chidhau: Explore the administrator dashboard and management pages for categories, brands, users, and orders using the available records, search functions and navigation menu to discover inconsistencies in displayed data, navigation and administrative record management.

## Product model (from step 1)

- Visitor can: Browse products, open product details, add products to cart, adjust the price range, sort alphabetically or by CO2 rating, filter by category, sustainability and brand, and access the contact page and bug hunting guide.
- Logged-in customer can: Access their account to manage their profile, favourites and orders, and access messages and invoices.
- Administrator can: View sales charts and recent orders; navigate to the brands, categories, products, orders and users management pages; search available records; and access editing and deletion controls where displayed. The extent of each operation has not yet been fully tested.
- Where money appears: Product prices appear in the homepage catalogue and on individual product pages. The cart displays item prices, item totals and the overall total. The team also identified an invoices section in the customer account.
- What this product is for: An online shop where customers, including people who use tools for work or home projects, can browse and buy tools.

## Session log

Session log with triage piles

Initial triage based on the supplied Lab 1 observations. REPORTABLE means a clear defect candidate to take to Step 2, not a claim that it has already been retested in Lab 2. Each owner must confirm their classifications and reproduce candidates before filing reports.

Row 21 was additionally confirmed by Tanaka in this conversation: logged in as customer@practicesoftwaretesting.com, 404 displayed in 10 of 10 selections and persisted after refresh.

REPORTABLE: clear defect candidate with a recorded route back to it.

ANOTHER LOOK: the expected behaviour, evidence or reproduction needs clarification.

NOT A DEFECT: use when intended behaviour or a misunderstanding has been established; no uncertain anomaly has been assigned this label here.

— (NOTE): supporting observation, outside the anomaly triage.

#

Mark

Area

What happened

How to get back to it

Pile

1

ANOMALY

Cart & checkout

Tanaka Zindi: Item line totals remain $00.00, including after changing quantities. The unit price displays correctly. For example, 3 Combination Pliers at $14.15 each should have a line total of $42.45. Observed both while logged out and while logged in as a customer.

Open Combination Pliers, add it to the cart, open the cart and change its quantity to 3. Observe the item's Total column. Repeat while logged out and while logged in.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

2

ANOMALY

Cart & checkout

Tanaka Zindi: Clicking the X button beside an item does not remove it from the cart. Observed both while logged out and while logged in as a customer.

Add Combination Pliers to the cart, open the cart and click the X beside the item. Observe that the item remains. Repeat while logged out and while logged in.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

3

NOTE

Cart & checkout

Tanaka Zindi: The overall cart total correctly accounts for product prices and quantities, despite the individual item totals displaying $00.00.

Add products to the cart, change their quantities and compare the overall cart total with the sum of each unit price multiplied by its quantity.

— (NOTE)

4

ANOMALY

Cart & checkout

Tanaka Zindi: While logged in, attempting to add another Combination Pliers with quantity 1 displayed “Oops, something went wrong.” The additional item was not added.

While logged in with Combination Pliers already in the cart, go to Categories → Hand Tools, filter for Pliers, open Combination Pliers and click Add to cart with quantity 1. Observe the error and inspect the cart.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

5

ANOMALY

Cart & checkout

Tanaka Zindi: While logged in, attempting to add Combination Pliers again reset existing cart quantities to 1 and reduced the overall total. In a follow-up, quantity 2 survived a refresh but reset to 1 after another add attempt from the homepage.

While logged in, set the cart quantity for Combination Pliers to 2, click outside the field and refresh. Confirm it remains 2. From the homepage, open Combination Pliers and attempt to add it again. Return to the cart and inspect the quantity.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

6

QUESTION

Cart & checkout

Tanaka Zindi: Entering 0, clearing the quantity field or entering 1.5 produces no apparent change to the cart calculation. It is unclear how the cart handles these inputs.

In the cart, try 0, a blank value and 1.5 in a quantity field. Record whether each value remains visible, whether a validation message appears and whether the overall total changes.

ANOTHER LOOK — Check validation and expected handling of zero, blank and fractional quantities separately.

7

NOTE

Cart & checkout

Tanaka Zindi: Refreshing the page after entering quantity 0 restores the previous quantity.

Change a cart quantity to 0, then refresh the page and inspect the quantity field.

— (NOTE)

8

NOTE

Cart & checkout

Tanaka Zindi: A valid cart quantity of 2 remained saved after clicking outside the field and refreshing the page while logged in.

Set Combination Pliers quantity to 2 in the cart, click outside the field, refresh and inspect the quantity.

— (NOTE)

9

ANOMALY

Checkout — Address

Tanaka Zindi: The green button at the bottom right of the Billing Address step has no visible text, leaving its purpose unclear.

Proceed through checkout to the Address step. Inspect the green button beneath the billing address fields.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

10

ANOMALY

Checkout — Payment

Tanaka Zindi: Bank transfer reaches an order confirmation displaying an invoice number. Cash on delivery, credit card, buy now pay later, gift card and the option labelled “error 304 missing payment gateway” display a payment-success message but remain on the payment form without showing that order confirmation.

Reach the Payment step, select a payment method, complete the displayed fields as needed and click Confirm. Compare the outcome for each listed method with the bank-transfer outcome. The notes do not establish whether every method was tested through a fresh checkout.

ANOTHER LOOK — Retest each payment method through a fresh checkout and check order creation.

11

ANOMALY

Checkout — Payment

Tanaka Zindi: Selecting Cash on Delivery displays bank-name and account-number fields that appear unrelated to paying on delivery. Whether these fields are mandatory was not established.

Proceed to the Payment step, select Cash on Delivery and inspect the bank-name and account-number fields beneath the dropdown.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

12

ANOMALY

Product Filters

Tanyaradzwa Mrewa: Under 'By brand', only 'Brand name 1' works. Checking the boxes for Brand name 2 through 10 results in an empty product list.

Go to Power Tools or Hand Tools category -> Check 'Brand name 2' in the left filter panel.

ANOTHER LOOK — Verify that products exist for each selected brand before treating empty results as a defect.

13

ANOMALY

Product Filters

Tanyaradzwa Mrewa: Under 'By category', checking 'Grinder' displays an empty page with no products, while Sander, Saw, and Drill work fine and display items.

Go to Power Tools category -> Check 'Grinder' in the left filter panel.

ANOTHER LOOK — Verify that Grinder products exist before treating an empty result as a defect.

14

ANOMALY

Product Filters

Tanyaradzwa Mrewa: The "Sort" dropdown is misspelled as "Sorth".

Look at the top of the left-hand panel on the homepage/category pages.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

15

ANOMALY

Product Filters

Tanyaradzwa Mrewa: The search box in the filters panel is misspelled as "Serch", and there is a broken image icon next to the "Search" heading.

Look at the left filter panel on any category page.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

16

ANOMALY

Product Filters

Tanyaradzwa Mrewa: Checking the 'Other' category filter displays heavy machinery (Excavator, Bulldozer, Crane). All of these items are marked "Out of stock" and do not have an "Add to cart" button.

Go to the homepage -> Check the 'Other' box in the left filter panel.

ANOTHER LOOK — Out-of-stock products may legitimately remain visible and unavailable to buy; check the expected rule.

17

QUESTION

Product Filters

Tanyaradzwa Mrewa: Should out-of-stock items (like the Long Nose Pliers or the Excavator) still show up when filtering, or should the filter hide them entirely?

Go to Hand Tools -> filter by Pliers -> look for Long Nose Pliers.

ANOTHER LOOK — Confirm whether filtering is supposed to hide out-of-stock products.

18

NOTE

Product Filters

Tanyaradzwa Mrewa: The Sustainability checkbox ("Show only eco-friendly products") successfully filters the list to only show items with the green ECO badge.

Go to any category -> check the sustainability box.

— (NOTE)

19

NOTE

Product Filters

Tanyaradzwa Mrewa: The Price Range slider resets to 0-200 whenever the page is refreshed or a different category is selected.

Change the price slider -> Refresh the page.

— (NOTE)

20

QUESTION

Admin / Category navigation

Vimbainashe Aulyn Chidhau: The Categories dropdown includes an entry labelled UNDEFINED. Opening it displays the heading "Category: Undefined" without visible product cards. Changing sorting options and filter checkboxes did not make products appear during the initial check. Hand Tools and Power Tools display product cards, but the reason for the empty Undefined category remains unknown.

Open the Toolshop application, select Undefined from the Categories dropdown, inspect the heading and product area, and try changing the sorting and filter controls. Compare the result with Categories → Hand Tools and Categories → Power Tools.

ANOTHER LOOK — Confirm what the Undefined entry should represent and isolate the menu-label problem.

21

ANOMALY

Category navigation — Chainsaws

Vimbainashe Aulyn Chidhau: Selecting the Chainsaws category displays a "404 Error — Page Not Found" page instead of the category content. The error persists after refreshing the page.

Open the Toolshop application, click Categories in the top navigation, select Chainsaws, and observe the 404 page. Press Ctrl + R and confirm that the same error remains.

REPORTABLE — Confirmed by Tanaka in 10 of 10 attempts; persists after refresh.

22

ANOMALY

Admin — Order status

Vimbainashe Aulyn Chidhau: Changing one order's status to COMPLETED changed other orders that previously had status SHIPPED to COMPLETED as well, while an order previously marked ON_HOLD remained unchanged. The cause has not been established.

Open Admin → Orders and record the initial statuses. Open an order previously marked SHIPPED, change its status to COMPLETED, and click Update status. Return to the Orders table and compare the statuses of the other orders.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

23

ANOMALY

Admin — Order status validation

Vimbainashe Aulyn Chidhau: Attempting to update an order previously marked ON_HOLD displayed the message Order was "on hold", status message must be set. The status message field was visible beneath the error.

Open Admin → Orders, select an order previously marked ON_HOLD, click Edit, attempt the status update and record the error. Inspect the Status Message field and whether the form explains what must be entered.

ANOTHER LOOK — A required status-message check may be intended; supply the message and retest.

24

ANOMALY

Admin — Brands search

Vimbainashe Aulyn Chidhau: Searching by the slug brand-name-4 displayed no brand rows. Searching by the name Brand name 4 displayed the full list rather than filtering to the matching record. Searching for a nonexistent brand name also left the full list visible. Clicking Reset cleared the search field while the table continued displaying all brands.

Open Admin → Brands. Search for brand-name-4, then reset and search for Brand name 4. Search for a nonexistent name. Finally, click Reset and observe the search field and table.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

25

NOTE

Admin — Categories search

Vimbainashe Aulyn Chidhau: The Categories search filtered the table correctly. Searching for hammer returned the Hammer record, while searching for saw returned Hand Saw and Saw. Clicking Reset cleared the search field and restored the full category table.

Open Admin → Categories. Search for hammer and inspect the results. Repeat with saw, then click Reset and verify that all category records reappear.

— (NOTE)

26

ANOMALY

Admin — Users search

Vimbainashe Aulyn Chidhau: Searching by first name, surname, or a combination of names returns inconsistent results. The search sometimes displays users whose names only partially match the entered query, while a completely unmatched query returns no records. The search may be matching parts of the query instead of the complete name.

Open Admin → Users. Search using different combinations of first names and surnames, including partial matches and completely unmatched names. Compare the displayed results against the entered search terms.

ANOTHER LOOK — Record exact queries and returned names, then confirm the intended matching rule.

27

ANOMALY

Admin — Products search

Vimbainashe Aulyn Chidhau: Searching for a specific product name returns the matching product at the top of the results, while other products containing the same keyword remain displayed below it. The search appears to prioritise the closest match rather than restrict the results to the specific product entered.

Open Admin → Products. Search for a general keyword that appears in multiple product names, then search for the complete name of one product in the results. Compare the displayed results and their order.

ANOTHER LOOK — Keyword or partial matching may be intended; confirm the search rule.

28

ANOMALY

Admin — Products input validation (stock and price)

Vimbainashe Aulyn Chidhau: The application accepts and saves negative values for both stock quantity and product price without displaying a validation error. Setting the stock quantity to -1 resulted in a “Product saved!” confirmation, and the negative value remained visible in the product table. Similarly, setting a product price to -12.01 was accepted and the negative price remained visible in the table. These results indicate that the application does not adequately validate negative stock quantities or prices.

Open Admin → Products. Edit a product with zero stock, change the stock quantity to -1, and click Save. Verify the success message and saved value. Then edit a product, enter a negative price such as -12.01, and click Save. Verify whether the negative price is saved and displayed in the product table.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

29

ANOMALY

Admin — Sales Reports

Vimbainashe Aulyn Chidhau: The year selection in the Average Sales per Month and Average Sales per Week reports only lists years from 2018 to 2025, despite the Orders table containing orders dated in 2026. As a result, users cannot select 2026 to view sales data for that year.

Open Admin → Orders and verify that orders exist with invoice dates in 2026. Navigate to Admin → Reports → Average Sales per Month and Average Sales per Week, then inspect the year dropdowns. Confirm that 2026 is missing from both reports.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

30

NOTE

Registration

Tinayeshe Mugwagwa: Submitting the registration form with every field blank shows a "required" error under each field (first name, last name, date of birth, address, postcode, city, phone).

Open Sign in → Register your account in a private window. Leave all fields blank and click Register.

— (NOTE)

31

QUESTION

Registration

Tinayeshe Mugwagwa: A blank Date of birth shows two errors at once: "Please enter a valid date in YYYY-MM-DD format." and "Date of Birth is required." Should an empty field also get the format error?

Open the registration form, leave Date of birth blank and click Register. Read the messages under Date of birth.

ANOTHER LOOK — Check whether showing both errors is contrary to the expected validation behaviour.

32

NOTE

Registration

Tinayeshe Mugwagwa: An e-mail without "@" (test) is rejected with "E-mail format is invalid."

On the registration form, enter test as E-mail address and click Register.

— (NOTE)

33

ANOMALY

Registration

Tinayeshe Mugwagwa: The password length error reads "Password must be minimal 10 characters long." The wording is incorrect (should be e.g. "at least 10 characters").

On the registration form, enter abc as Password and click Register. Read the message under Password.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

34

ANOMALY

Registration — security

Tinayeshe Mugwagwa: Registering with an e-mail that already has an account shows "User already registered - Your password hint is: Name of your cat!" This confirms to anyone that the e-mail is registered and reveals that account's password hint without any login.

Fill in all registration fields with valid data, use customer@practicesoftwaretesting.com as E-mail and any 10-character password, click Register. Read the error under the button.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

35

ANOMALY

Registration — visual

Tinayeshe Mugwagwa: The "User already registered" error is displayed in a serif font, unlike the rest of the form.

Reproduce row 34 and compare the error text font with the field labels.

ANOTHER LOOK — Check whether the font difference is an unintended inconsistency or deliberate error styling.

36

QUESTION

Registration

Tinayeshe Mugwagwa: The State field is a dropdown that showed "Poland", which is a country, not a state. What is this field meant to contain?

Open the registration form, enter Poland as Country and open the State dropdown.

ANOTHER LOOK — Confirm the intended State field values and record its options.

37

QUESTION

Registration — security

Tinayeshe Mugwagwa: The password abcdefghij (10 lowercase letters, no digits or symbols) was accepted and the account was created. Only length appears to be checked. Is this the intended password policy?

Register a new account (I used tina.test1026@example.com) with all fields valid and password abcdefghij. Observe that registration succeeds.

ANOTHER LOOK — Confirm the password policy; accepting a lowercase password alone does not establish a defect.

38

NOTE

Login

Tinayeshe Mugwagwa: A wrong password shows the generic "Invalid email or password", which does not reveal whether the account exists (unlike registration, row 34). Whether repeated failures cause a lockout was not confirmed.

Sign in with tina.test1026@example.com and password wrongpass123. Read the message.

— (NOTE)

39

ANOMALY

Login — visual

Tinayeshe Mugwagwa: On the Login page the e-mail text touches the left edge of its box with no padding, and the password box and Login button are narrower than the e-mail box.

Open Sign in, type any e-mail and password and compare the field and button widths and the text position.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

40

NOTE

Session

Tinayeshe Mugwagwa: After signing out, pressing the browser Back button 2–3 times does not show account pages again.

Log in, open My account, sign out, then press Back several times.

— (NOTE)

41

QUESTION

Session

Tinayeshe Mugwagwa: Signing out in one window does not end the session in another window logged into the same account; the first window can still open Profile and Favourites. Should logout end all sessions?

Log in as the same account in a normal window and a private window. Sign out in the private window. In the normal window click Profile or Favourites.

ANOTHER LOOK — Confirm whether logout should end only the current session or all sessions.

42

ANOMALY

Account — Profile

Tinayeshe Mugwagwa: Clicking Update Profile shows "Resource not found" and nothing is saved. This happens both with invalid data (first name Ñandú <b>bold</b>, phone abc123) and with valid data (first name Tina2, last name Mugwagwa, city Lublin, phone 535000000). No profile change can be saved.

Log in as tina.test1026@example.com / abcdefghij, open My account → Profile, change the first name to Tina2, click Update Profile, then refresh.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

43

ANOMALY

Account — Profile

Tinayeshe Mugwagwa: The Last Name field on the Profile page shows the first name entered at registration (Tawana) instead of the last name (Mugwagwa). The correct full name is stored (see row 50), so the Profile page displays the wrong value.

Register with first name Tawana and last name Mugwagwa, log in, open My account → Profile and read the Last Name field.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

44

ANOMALY

Account — Profile

Tinayeshe Mugwagwa: The City field on the Profile page shows "City not found" although Lublin was entered at registration.

Register with city Lublin, log in, open My account → Profile and read the City field.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

45

NOTE

Account — Profile

Tinayeshe Mugwagwa: The Profile page shows Country as PL and State as Poland, while Country was entered as Poland at registration.

Register with Country Poland, then open My account → Profile and compare Country and State.

— (NOTE)

46

ANOMALY

Navigation — text

Tinayeshe Mugwagwa: The top-menu link to the contact page reads "Contakt" instead of "Contact".

Open any page and read the top navigation menu.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

47

ANOMALY

Contact — text

Tinayeshe Mugwagwa: The placeholder in the Message box reads "Massage" instead of "Message".

Open the contact page and look at the empty Message box.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

48

ANOMALY

Navigation — visual

Tinayeshe Mugwagwa: The logo at the top left of every page is a broken image icon.

Open any page and look at the top-left corner of the navigation bar.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

49

ANOMALY

Contact — visual

Tinayeshe Mugwagwa: The "Attachment" label on the contact form uses a serif font, unlike the other labels.

Open the contact page and compare the Attachment label with the Subject and Message labels.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

50

NOTE

Contact

Tinayeshe Mugwagwa: When logged in, the contact page greets the user correctly ("Hello Tawana Mugwagwa"), so registration saved the correct first and last name.

Log in as tina.test1026@example.com and open the contact page.

— (NOTE)

51

ANOMALY

Navigation — account menu

Tinayeshe Mugwagwa: When logged in, the account menu at the top right is labelled "User Data not found" instead of the user's name, although the contact page shows the name correctly (row 50).

Log in as tina.test1026@example.com and read the account menu label at the top right (zoom out with Ctrl − if it is cut off).

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

52

ANOMALY

Navigation

Tinayeshe Mugwagwa: Clicking Home in the top menu opens the contact page instead of the product catalogue. Observed while logged out and while logged in. Products could only be reached through Categories.

Click Home in the top menu and check the page heading and the address bar. Repeat after logging in.

REPORTABLE — Clear candidate from Lab 1; reproduce again before filing.

53

NOTE

Contact

Tinayeshe Mugwagwa: Sending a contact message while logged in shows "Thanks for your message! We will contact you shortly."

Log in, open the contact page, choose a subject, type a message and click Send.

— (NOTE)

54

NOTE

Account — Messages

Tinayeshe Mugwagwa: The sent message appears under My account → Messages with status NEW and a Details button.

After row 53, open the account menu → My account → Messages.

— (NOTE)

55

QUESTION

Account — Messages

Tinayeshe Mugwagwa: The message is dated 2026-10-26 18:26:54, about one hour earlier than the local time it was sent (≈19:26 in Poland). Is the site showing UTC instead of the user's local time?

Send a contact message, note your local time, then open My account → Messages and compare the Date column.

ANOTHER LOOK — Establish the displayed timezone before reporting a time discrepancy.

56

NOTE

Account — Messages

Tinayeshe Mugwagwa: The Subject column shows the internal value customer-service rather than a readable label such as "Customer service".

After row 53, open My account → Messages and read the Subject column.

— (NOTE)

57

NOTE

Account — Favourites

Tinayeshe Mugwagwa: Clicking Add to favourites twice on Combination Pliers lists the product once in Favourites, with no duplicate. The messages shown after each click were not recorded.

Log in, go to Categories → Hand Tools → Combination Pliers, click Add to favourites twice, then open My account → Favourites.

— (NOTE)

## Debrief[individual findings]

### Tanaka Zindi

1. **Covered / not covered:** I explored cart quantities, item removal, adding an existing product again, refreshing the cart, the billing-address step and the available payment methods. I checked the initial cart problems both while logged out and while logged in. I did not test blank billing fields or confirm whether the banking fields shown for Cash on Delivery were mandatory.
2. **What we found:** Individual item totals remained $00.00, although the overall cart total calculated correctly. The X buttons did not remove items. Adding Combination Pliers again produced an error and reset existing quantities to 1, reducing the cart total. The address step had an unlabelled green button. Only bank transfer reached an order confirmation with an invoice number; the other payment options displayed a success message but stayed on the payment form. Cash on Delivery also displayed banking fields. The quantity resets could cause customers to order fewer items than intended, while the missing confirmation leaves the order outcome unclear.
3. **What got in the way:** The broken removal buttons made it difficult to prepare an empty cart. Adding an existing product again reset quantities and disrupted my test setup. The unlabelled address button made its purpose unclear. For some payment methods, I could not establish whether the success message meant an order had been created.
4. **What we learned:** A correct overall cart total does not mean every item total displays correctly. A valid quantity of 2 survived a refresh, but an attempt to add Combination Pliers again reset it to 1. The checkout outcome also differed depending on the payment method selected.
5. **Next charter should be:** Explore billing and payment validation with blank and invalid inputs to discover whether checkout prevents incomplete submissions and clearly explains what needs correcting.

### Tanyaradzwa Mrewa

1. **Covered / not covered:** I covered the product filtering system, specifically the brand checkboxes, category filters, price slider, search box, and the sorting dropdown. I did not test combining multiple filters at once or the behaviour of the filter panel on mobile screens.
2. **What we found (my area):** I found several serious anomalies. 9 out of 10 Brand filters are broken and return empty results. The 'Grinder' category is broken. The 'Other' category shows out-of-stock heavy machinery with no way to buy them. I also found multiple UI typos ("Sorth", "Serch") and a broken image icon.
3. **What got in the way:** Placeholder data made it difficult. Because brands are just named "Brand name 2", "Brand name 3", etc., it is hard to know if a filter is broken or if the backend simply has no products for that brand.
4. **What we learned:** The filtering system has backend data issues (missing products) and front-end display bugs (typos, broken icons).
5. **Next charter should be:** Explore the checkout flow and cart management to discover calculation errors and validation issues.

### Tinayeshe Mugwagwa 

1. **Covered / not covered:** I explored registration validation (blank fields, invalid e-mail, short password, an already-registered e-mail and a weak 10-letter password), login with a wrong password, logout followed by the Back button, two simultaneous sessions, profile editing, the contact form with the Messages page, and adding a favourite. I did not test changing the password, "Forgot your Password?", removing favourites, contact attachments or very long messages, or invoices (my new account had no orders). I did not confirm whether repeated failed logins cause a lockout. Across the team, nobody tested the language switcher, the mobile layout or invoice details and downloads.
2. **What we found (my area):** 28 entries: 13 anomalies, 5 questions and 10 notes (rows 30–57). The most serious are row 34, where registration reveals that an e-mail is registered and shows that account's password hint to anyone, and row 42, where Update Profile always fails with "Resource not found", so customers cannot correct their details. Row 52 is also significant: the Home link opens the contact page, so customers cannot return to the catalogue from the menu. Rows 43, 44 and 51 show account pages displaying the wrong name and city, or "User Data not found".
3. **What got in the way:** The Home link opening the contact page meant I had to reach products through Categories. Because profile updates always fail, I could not tell whether invalid input such as letters in the phone number would be rejected or saved. My new account had no orders, so I could not check invoices.
4. **What we learned:** Registration checks format and length well, but it accepts weak passwords and leaks account information when the e-mail already exists. The correct name is stored (the contact page shows it), yet the profile page and account menu display it wrongly, so the problem seems to be in how account pages read user data rather than in registration.
5. **Next charter should be:** Explore the profile, password-change and forgot-password pages with valid and invalid edits, comparing what the profile page, account menu and contact page show, to discover where user data is lost or displayed incorrectly.

### Vimbainashe Aulyn Chidhau 

1. **Covered / not covered:** I explored the administrator pages, focusing on Categories, Brands, Users, Orders, Products and Sales Reports. I tested search functions, category navigation , order-status updates, product input validation and the year the selectors in the sales reports. i also inspected the Add User form and compared the behaviour of search functions across different pages. I did not test every administrator function, all possible input values, user permissions or the underlying causes of the problems found.
2. **What we found (my area):**  I found several potential defects in the administrator area. Selecting Chainsaws displayed a 404 error, and changing one's order's status to COMPLETED appeared to change other orders that were previously SHIPPED. The Brands and Users search functions also returned inconsistent results.In Products, the application accepted and saved negative stock quantities and negative prices without showing a validation error. Both sales reports only allowed years from 2018 to 2025, even though the Orders table contained dates from 2026. However, the Categories search worked correctly, returning matching results and restoring the full list when Reset was used. Selecting the Undefined category displayed no products, but I could not confirm whether this was a defect because the expected behaviour was unclear.
3. **What got in the way:** The inconsistent search results made it difficult to determine whether the administrator pages were filtering records correctly. The order-status behaviour also made it difficult to trust that changing one order would affect only that order. Some expected behaviours were unclear, particularly the Undefined category and the requirement to enter a status message when updating an order that was ON_HOLD. I could observe the problems, but I could not determine their technical causes during the exploratory session.
4. **What we learned:** I learned that administrator functions need to be checked for both correct individual behaviour and consistency across records. A successful save message does not necessarily mean that the entered data is valid, as negative stock quantities and prices were accepted. I also learned that search functions on similar pages may behave differently, and that changing one order's status should be checked against other orders to identify unintended changes. Comparing the sales-report year selectors with the dates in the Orders table helped reveal a limitation that was not obvious when viewing the reports alone.
5. **Next charter should be:** Explore administrator record management using multiple orders, different search terms and invalid product values to discover whether changes affect only the intended records and whether the system correctly validates inputs and displays clear error messages.

## Debrief Summary[group findings]

**1. Covered / not covered:**

As a team, we explored four main areas of the Toolshop application: cart and checkout, product filtering, registration and customer account management, and administrator functions. We tested cart quantities, item removal and payment methods; product filters for brands, categories, sustainability and price range; registration validation, login, profile editing, contact forms and favourites; and administrator searches, order-status updates, product validation and sales reports. However, we did not cover every possible input or combination of filters, password recovery, all invoice functions, mobile responsiveness, the language switcher or every administrator function. Further testing is needed in these areas.

**2. What we found (team findings):**

We identified several anomalies across the application. In the cart and checkout, individual item totals displayed $00.00, item removal did not work correctly, adding an existing product could reset quantities, and payment methods produced inconsistent confirmation outcomes. In product filtering, most of the tested brand filters returned empty results, the Grinder filter displayed no products, and the interface contained spelling errors and a broken image. The Other category also displayed out-of-stock heavy machinery without an Add to cart option. In registration and account management, we found that weak passwords could be accepted, an existing email address could reveal account-related information, profile updates failed with a “Resource not found” message, and some account pages displayed incorrect user details. In the administrator area, selecting Chainsaws produced a 404 error, Brands and Users searches behaved inconsistently, changing an order's status appeared to affect other orders, negative stock quantities and prices were accepted, and sales reports did not offer 2026 despite orders dated in that year. Some observations, including the behaviour of the Undefined category and the display of out-of-stock products, require clarification before they can be confirmed as defects.

**3. What got in the way:**

Our testing was sometimes disrupted by broken controls, inconsistent navigation and unexpected changes to application data. In the cart, item removal and quantity resets made it harder to prepare and maintain a consistent test setup. In product filtering, placeholder brand names and empty results made it difficult to determine whether the problem was caused by missing product data or incorrect filtering. In registration and account management, failed profile updates prevented further testing of some invalid inputs, while the lack of orders in a newly created account limited invoice testing. In the administrator area, inconsistent search results and unclear expected behaviour made it difficult to decide whether certain observations were defects. These obstacles limited the depth of some tests and highlighted the need for further investigation.

**4. What we learned:**

We learned that testing should examine complete workflows as well as individual features. A correct overall cart total does not guarantee that item totals are displayed correctly, and a success message does not always mean that an operation has completed as expected. We also learned that product filters must be checked against the products they should return, while registration and account-management functions must protect user information, validate inputs and display accurate details consistently. In the administrator area, changes to one order should be checked against other records, and saved product values should be validated rather than accepted without restriction. Comparing similar functions across the application helped us identify inconsistencies, distinguish confirmed observations from unanswered questions, and decide which areas need further testing.

**5. Next charter should be:**

Our next charter should focus on **validating important customer and administrator workflows using valid, invalid and boundary-value inputs**. We should explore product filtering with individual and combined filters, registration and profile management with different email and password inputs, cart and checkout behaviour with different quantities and payment methods, and administrator updates involving multiple orders and invalid product values. The aim should be to discover whether the application validates data correctly, protects customer information, returns accurate results, changes only the intended records and clearly communicates errors and successful operations.


## Debrief Evidence

The screenshot uploaded provides supporting evidence of our team's debrief discussion.

![Team debrief discussion](debrief-screenshot.png)
