# Checklist — Cart

Page: `/view_cart`, Add to cart from `/products` and `/product_details/{id}`

Result legend: ✅ Pass · ❌ Fail · ⏳ Not run yet

| # | Check | Result |
|---|---|---|
| 1 | Add to cart from the product listing shows the "Added!" modal with View Cart / Continue Shopping | ✅ |
| 2 | Add to cart from the product page adds the quantity entered in the field | ✅ |
| 3 | Adding the same product twice increases its quantity (no duplicate rows) | ✅ |
| 4 | Line total = price × quantity | ✅ |
| 5 | Quantity 0 or negative cannot be added | ❌ [BUG-001](../bug-reports/BUG-001-negative-quantity-in-cart.md) |
| 6 | Total is never negative | ❌ [BUG-001](../bug-reports/BUG-001-negative-quantity-in-cart.md) |
| 7 | Very large quantity (e.g. 99999) is limited or rejected | ⏳ |
| 8 | Remove (×) deletes the line without page reload | ✅ |
| 9 | Empty cart shows "Cart is empty! Click here to buy products." | ✅ |
| 10 | Cart content persists when navigating between pages | ✅ |
| 11 | Guest cart is kept after login | ⏳ |
| 12 | "Proceed To Checkout" as guest shows the Register / Login modal | ✅ |
| 13 | Product name in the cart links to the product page | ✅ |
| 14 | Add to cart on a non-existent product gives feedback instead of silently failing | ❌ [BUG-002](../bug-reports/BUG-002-nonexistent-product-empty-page.md) |
