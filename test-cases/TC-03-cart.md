# Test Cases — Cart

Status legend: **Pass** · **Fail** · **Not run**

| ID | Title | Preconditions | Steps | Test data | Expected result | Priority | Status |
|---|---|---|---|---|---|---|---|
| TC-CART-01 | Add product from listing | Cart empty | 1. Open `/products`<br>2. Hover the first card, click Add to cart<br>3. Click View Cart | Blue Top, Rs. 500 | "Added!" modal; cart has Blue Top, qty 1, total Rs. 500 | P1 | Pass |
| TC-CART-02 | Add product with custom quantity | Cart empty | 1. Open `/product_details/1`<br>2. Set quantity 4<br>3. Add to cart, View Cart | qty 4 | Cart line qty 4, total Rs. 2000 | P1 | Pass |
| TC-CART-03 | Same product added twice | Cart empty | 1. Add Men Tshirt twice | Men Tshirt, Rs. 400 | One line, qty 2, total Rs. 800 | P2 | Pass |
| TC-CART-04 | Negative quantity | Cart empty | 1. Open `/product_details/1`<br>2. Set quantity `-3`<br>3. Click Add to cart<br>4. Open cart | qty −3 | Validation message; product is not added | P1 | **Fail** → [BUG-001](../bug-reports/BUG-001-negative-quantity-in-cart.md) |
| TC-CART-05 | Zero quantity | Cart empty | Same as TC-CART-04 with `0` | qty 0 | Validation message; product is not added | P1 | **Fail** → [BUG-001](../bug-reports/BUG-001-negative-quantity-in-cart.md) |
| TC-CART-06 | Remove a line | Cart has 2 products | 1. Click × on the second line | — | Line disappears without reload; other line stays | P1 | Pass |
| TC-CART-07 | Remove last line | Cart has 1 product | 1. Click × | — | "Cart is empty! Click here to buy products." | P2 | Pass |
| TC-CART-08 | Guest proceeds to checkout | Logged out; cart not empty | 1. Click Proceed To Checkout | — | Modal "Register / Login account to proceed on checkout" with link to `/login` | P1 | Pass |
| TC-CART-09 | Cart persists after login | Logged out; cart has 1 product | 1. Log in<br>2. Open cart | Valid account | Guest cart content is still in the cart | P2 | Not run |
| TC-CART-10 | Product link in cart | Cart not empty | 1. Click the product name in the cart | — | Product details page of that product opens | P3 | Pass |
