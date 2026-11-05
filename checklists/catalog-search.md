# Checklist — Catalog and Search

Pages: `/products`, `/product_details/{id}`, `/category_products/{id}`, `/brand_products/{name}`

Result legend: ✅ Pass · ❌ Fail · ⏳ Not run yet

## Product listing

| # | Check | Result |
|---|---|---|
| 1 | "All Products" page lists products with image, name, price, Add to cart and View Product | ✅ |
| 2 | Category sidebar expands Women / Men / Kids and lists sub-categories | ✅ |
| 3 | Category page title matches the selected category (e.g. "Women - Tops Products") | ✅ |
| 4 | Brand counters in the sidebar match the number of products on each brand page | ✅ |
| 5 | Brand page title shows the brand name | ✅ |
| 6 | Non-existent category / brand shows a clear "not found" state | ❌ Shows an empty listing with HTTP 200 |

## Product details

| # | Check | Result |
|---|---|---|
| 7 | Product page shows name, category, price, availability, condition, brand | ✅ |
| 8 | Quantity field defaults to 1 | ✅ |
| 9 | Quantity below 1 is rejected | ❌ [BUG-001](../bug-reports/BUG-001-negative-quantity-in-cart.md) |
| 10 | "Write Your Review" form is present with Name, Email, Review | ✅ |
| 11 | Non-numeric product id (`/product_details/abc`) returns a 404 page | ✅ |
| 12 | Unknown numeric product id (`/product_details/9999`) returns a 404 / "product not found" page | ❌ [BUG-002](../bug-reports/BUG-002-nonexistent-product-empty-page.md) |

## Search

| # | Check | Result |
|---|---|---|
| 13 | Search by full product name returns that product ("blue top" → Blue Top) | ✅ |
| 14 | Search is case-insensitive ("top" = "Top" = "TOP") | ✅ |
| 15 | Search by partial word returns all matching products ("jeans" → 3) | ✅ |
| 16 | Page title changes to "Searched Products" | ✅ |
| 17 | Empty search shows all products | ✅ |
| 18 | Leading / trailing spaces are ignored | ❌ [BUG-005](../bug-reports/BUG-005-search-not-trimmed.md) |
| 19 | No matches shows a "no products found" message | ❌ Empty grid, no message (see BUG-005 notes) |
| 20 | Special characters (`%`, `<b>`) do not break the page and are not rendered as HTML | ✅ |
| 21 | Word order variations ("top blue") return the same product | ❌ 0 results (logged as improvement, not a defect) |
