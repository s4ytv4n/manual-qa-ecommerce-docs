# Checklist — Checkout

Pages: `/checkout`, `/payment`, `/payment_done/{id}`

Precondition: logged-in test user with at least one product in the cart.

Result legend: ✅ Pass · ❌ Fail · ⏳ Not run yet

## Review step

| # | Check | Result |
|---|---|---|
| 1 | Guest clicking "Proceed To Checkout" is asked to register / login | ✅ |
| 2 | Delivery address matches the address entered at registration | ⏳ |
| 3 | Billing address matches the address entered at registration | ⏳ |
| 4 | "Review Your Order" lists every cart line with correct quantity and line total | ⏳ |
| 5 | Order total equals the sum of line totals | ⏳ |
| 6 | Checkout is blocked when the cart contains a quantity below 1 or the total is not positive | ⏳ (relates to BUG-001) |
| 7 | Comment textarea accepts text and keeps it on Place Order | ⏳ |
| 8 | Direct access to `/checkout` with an empty cart is handled gracefully | ⏳ |

## Payment step

| # | Check | Result |
|---|---|---|
| 9 | Name on Card, Card Number, CVC, Expiration month and year are required | ⏳ |
| 10 | Card number accepts digits only and validates length | ⏳ |
| 11 | CVC accepts 3–4 digits only | ⏳ |
| 12 | Expired card date (past month / year) is rejected | ⏳ |
| 13 | Month accepts 01–12 only | ⏳ |
| 14 | "Pay and Confirm Order" shows "ORDER PLACED!" | ⏳ |
| 15 | Double click on "Pay and Confirm Order" does not create two orders | ⏳ |
| 16 | "Download Invoice" downloads a file with the correct total | ⏳ |
| 17 | Cart is empty after a successful order | ⏳ |
| 18 | Browser Back after order does not resubmit payment | ⏳ |

> Payment checks use only dummy data. The store has no real payment provider.
