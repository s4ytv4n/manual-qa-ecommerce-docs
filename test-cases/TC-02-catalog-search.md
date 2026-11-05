# Test Cases — Catalog and Search

Status legend: **Pass** · **Fail** · **Not run**

| ID | Title | Preconditions | Steps | Test data | Expected result | Priority | Status |
|---|---|---|---|---|---|---|---|
| TC-CAT-01 | All Products page | — | 1. Click Products in the header | — | "All Products" title; every card has image, name, price, Add to cart, View Product | P1 | Pass |
| TC-CAT-02 | Product details page content | — | 1. Open `/products`<br>2. Click View Product on the first card | Product 1 (Blue Top) | Page shows name, category, price, quantity (default 1), Add to cart, availability, condition, brand | P1 | Pass |
| TC-CAT-03 | Filter by category | — | 1. Expand Women in the sidebar<br>2. Click Dress | — | Title "Women - Dress Products"; only dresses are listed | P2 | Pass |
| TC-CAT-04 | Brand counters match brand pages | — | 1. For each brand in the sidebar compare the counter with the number of products on the brand page | All 8 brands | Counter equals the number of listed products for every brand | P3 | Pass |
| TC-CAT-05 | Unknown product id | — | 1. Open `/product_details/9999` | id 9999 | 404 page or "Product not found" message; no Add to cart | P2 | **Fail** → [BUG-002](../bug-reports/BUG-002-nonexistent-product-empty-page.md) |
| TC-CAT-06 | Non-numeric product id | — | 1. Open `/product_details/abc` | `abc` | HTTP 404 page | P3 | Pass |
| TC-CAT-07 | Unknown category id | — | 1. Open `/category_products/999` | id 999 | Not-found message | P3 | **Fail** — empty listing with broken heading "-  Products", HTTP 200 |
| TC-SRCH-01 | Search by exact product name | — | 1. Open `/products`<br>2. Type the name in Search Product<br>3. Click search | `blue top` | Title "Searched Products"; Blue Top is listed | P1 | Pass |
| TC-SRCH-02 | Search is case-insensitive | — | 1. Search `top`, then `Top`, then `TOP` | — | Same 14 results for all three | P2 | Pass |
| TC-SRCH-03 | Search ignores leading / trailing spaces | — | 1. Search `top`<br>2. Search ` top ` (spaces around) | — | Same result set for both queries | P3 | **Fail** → [BUG-005](../bug-reports/BUG-005-search-not-trimmed.md) |
| TC-SRCH-04 | Search with no matches | — | 1. Search a string that matches nothing | `xyzqwe` | "No products found" message | P3 | **Fail** — empty grid, no message (BUG-005 notes) |
| TC-SRCH-05 | Search with special characters | — | 1. Search `%`<br>2. Search `<b>x</b>` | — | Page loads; input is shown as text, not rendered as HTML; no server error | P2 | Pass |
| TC-SRCH-06 | Empty search | — | 1. Click search with an empty field | — | All products are shown | P3 | Pass |
