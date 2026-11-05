# Test Cases — Checkout

Status legend: **Pass** · **Fail** · **Not run**

Payment checks use dummy data only; the store has no real payment provider.

| ID | Title | Preconditions | Steps | Test data | Expected result | Priority | Status |
|---|---|---|---|---|---|---|---|
| TC-CHK-01 | Place order as registered user (happy path) | Logged in; cart has 2 products | 1. Open cart, click Proceed To Checkout<br>2. Check addresses and order review<br>3. Enter a comment, click Place Order<br>4. Fill payment form, click Pay and Confirm Order | Dummy card data | "ORDER PLACED!"; cart is empty afterwards | P1 | Not run |
| TC-CHK-02 | Address details on review step | Logged in with known address | 1. Proceed to checkout | Address from registration | Delivery and billing address match the registration data exactly | P1 | Not run |
| TC-CHK-03 | Order total on review step | Logged in; cart: Blue Top ×2, Men Tshirt ×1 | 1. Proceed to checkout | Rs. 500×2 + Rs. 400 | Line totals Rs. 1000 and Rs. 400; Total Amount Rs. 1400 | P1 | Not run |
| TC-CHK-04 | Checkout with invalid cart quantity | Logged in; cart contains a line with qty −3 (BUG-001) | 1. Proceed to checkout | — | Checkout is blocked until quantities are corrected; total is never negative | P1 | Not run |
| TC-CHK-05 | Payment form required fields | On `/payment` | 1. Click Pay and Confirm Order with empty fields | — | Not submitted; required-field message for each empty field | P1 | Not run |
| TC-CHK-06 | Expired card | On `/payment` | 1. Enter expiration in the past<br>2. Submit | MM 01, YYYY 2020 | Payment rejected with "card expired" message | P2 | Not run |
| TC-CHK-07 | Non-numeric card number and CVC | On `/payment` | 1. Enter letters in Card Number and CVC<br>2. Submit | `abcd` | Validation message; not submitted | P2 | Not run |
| TC-CHK-08 | Download invoice | Order placed (TC-CHK-01) | 1. Click Download Invoice | — | Invoice file downloads and shows the correct name and total | P2 | Not run |
| TC-CHK-09 | Double submit protection | On `/payment` with valid data | 1. Double-click Pay and Confirm Order | — | Exactly one order is created | P2 | Not run |
