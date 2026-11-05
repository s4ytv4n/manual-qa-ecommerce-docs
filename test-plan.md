# Test Plan — automationexercise.com

| | |
|---|---|
| **Document ID** | TP-AE-001 |
| **Version** | 1.0 |
| **Author** | Ivan (QA Engineer) |
| **Date** | 2026-11-05 |
| **System under test** | https://automationexercise.com (public demo e-commerce store) |

## 1. Purpose

Describe the scope, approach, environment and exit criteria for manual functional testing of the core customer journeys of an e-commerce storefront: account access, product discovery, cart, checkout and customer contact.

The site is a public practice store, so this plan is written the way it would be for a real client project, with the limits of a demo target stated openly in section 9.

## 2. Scope

### In scope

| Area | Features |
|---|---|
| Registration and login | Signup form, account details form, login, logout, delete account, error messages for invalid / existing credentials |
| Catalog and search | All Products page, product details, categories (Women / Men / Kids), brands, search, error handling for invalid product URLs |
| Cart | Add from listing and from product page, quantity handling, aggregation of the same product, line totals, remove item, cart persistence across pages |
| Checkout | Proceed to checkout as guest and as logged-in user, address review, order comment, payment form, order confirmation, invoice download |
| Contact form | Required fields, email validation, file attachment, confirmation dialog, success message |
| Cross-cutting | Footer subscription, navigation, HTTP status of missing pages |

### Out of scope

- Performance and load testing (covered by a separate load-testing activity).
- Security / penetration testing beyond basic input-handling checks.
- Automated regression (covered by the [Playwright](https://github.com/s4ytv4n/playwright-ecommerce-framework) and [Selenium](https://github.com/s4ytv4n/selenium-java-ecommerce-framework) portfolio frameworks).
- Real payment processing: the store has no real payment provider.
- Third-party advertising content shown on the site.

## 3. Test approach

| Technique | Where it is used |
|---|---|
| Checklist-based testing | Fast coverage of every feature area (see [checklists](checklists/)) |
| Scenario-based test cases | Main positive and negative flows with explicit steps and expected results (see [test cases](test-cases/)) |
| Equivalence partitioning and boundary values | Quantity field (−1, 0, 1, large values), text field lengths, search input |
| Error guessing / exploratory sessions | Invalid URLs, leading / trailing whitespace, empty optional fields, file upload |
| Network and DOM inspection (DevTools) | Confirming root cause of defects (status codes, request payloads, form attributes) |

Test levels: system testing through the UI, supported by DevTools for evidence. Test types: functional, negative, UI / usability, basic compatibility.

## 4. Test environment

| Item | Value |
|---|---|
| URL | https://automationexercise.com |
| OS | Windows 11 x64 |
| Browser | Google Chrome (latest stable) |
| Viewport | 1920×1080 desktop |
| Tools | Chrome DevTools (Elements, Network, Console), Markdown for documentation, GitHub for defect / doc storage |
| Test data | Disposable test emails on `example.com`; no real personal or payment data |

## 5. Entry criteria

- Site is reachable and the home page loads without server errors.
- Test plan, checklists and test cases are reviewed.
- Test data is prepared.

## 6. Exit criteria

- 100% of planned test cases executed (or explicitly marked Blocked / Not run with a reason).
- No open Critical defects; every High defect has an agreed fix plan.
- All found defects are reported with steps, expected / actual results and evidence.
- Test summary is published in the [README](README.md#execution-summary).

## 7. Defect management

Defects are documented in [bug-reports](bug-reports/) using one template.

| Severity | Meaning |
|---|---|
| Critical | Blocks a core journey or causes data loss / financial loss; no workaround |
| High | Core function produces wrong results (e.g. wrong totals); workaround is unreliable |
| Medium | Feature works incorrectly in a non-blocking way, or bad handling of invalid input |
| Low | Cosmetic, usability or minor consistency issue |

Priority (P1–P3) reflects how soon the business should fix it and is set separately from severity.

## 8. Deliverables

| Deliverable | Location |
|---|---|
| Test plan | this document |
| Checklists | [checklists/](checklists/) |
| Test cases | [test-cases/](test-cases/) |
| Bug reports with screenshots | [bug-reports/](bug-reports/) |
| Execution summary | [README.md](README.md#execution-summary) |

## 9. Risks and assumptions

| Risk / assumption | Mitigation |
|---|---|
| Public demo site: no specification, shared by many testers, content may change at any time | Expected results are based on common e-commerce behaviour and on the site's own HTML attributes (e.g. `min="1"`); every defect has a date and environment |
| Shared backend: accounts and data may be created or deleted by other users | Use unique disposable test emails; do not rely on pre-existing data |
| Advertising iframes can overlap elements and change layout | Close or ignore ads; never report ad content as a defect |
| No real payment provider | Payment form is tested for field validation and flow only |

## 10. Schedule

| Activity | Effort |
|---|---|
| Analysis and test plan | 0.5 day |
| Checklists and test cases | 1 day |
| Execution and exploratory sessions | 1 day |
| Defect reporting and summary | 0.5 day |
