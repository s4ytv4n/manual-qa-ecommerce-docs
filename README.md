# Manual QA documentation: e-commerce demo store

Manual testing documentation for the public demo store [automationexercise.com](https://automationexercise.com): test plan, checklists, test cases and real bug reports found on the live site.

It shows how I work on client e-commerce projects before (and alongside) automation: understand the shop's main customer journeys, plan coverage, test by hand, and report defects so that a developer can reproduce and fix them without asking questions.

## Contents

| Document | What it covers |
|---|---|
| [Test plan](test-plan.md) | Scope, approach, environment, entry / exit criteria, severity scale, risks |
| [Checklists](checklists/) | Fast coverage of 5 areas: [registration / login](checklists/registration-login.md), [catalog and search](checklists/catalog-search.md), [cart](checklists/cart.md), [checkout](checklists/checkout.md), [contact form](checklists/contact-form.md) |
| [Test cases](test-cases/) | 51 test cases in table form with preconditions, steps, data, expected result, priority and status |
| [Bug reports](bug-reports/) | 5 defects found on the live site, each with steps, expected / actual result, annotated screenshot and root-cause notes |

## Bugs found

| ID | Title | Severity |
|---|---|---|
| [BUG-001](bug-reports/BUG-001-negative-quantity-in-cart.md) | Cart accepts zero and negative quantity, line total becomes negative | High |
| [BUG-002](bug-reports/BUG-002-nonexistent-product-empty-page.md) | Non-existent product id opens an empty product page (HTTP 200) with a dead Add to cart button | Medium |
| [BUG-003](bug-reports/BUG-003-contact-form-empty-message.md) | Contact form is submitted successfully with empty Name, Subject and Message | Medium |
| [BUG-004](bug-reports/BUG-004-contact-form-attachment-not-sent.md) | Contact form attachment is never sent: form is missing `enctype="multipart/form-data"` | Medium |
| [BUG-005](bug-reports/BUG-005-search-not-trimmed.md) | Product search does not trim leading spaces: " top" returns fewer results than "top" | Low |

## Execution summary

Executed on 2026-11-05, Windows 11, Chrome (latest stable), 1920×1080.

| Area | Test cases | Pass | Fail | Not run |
|---|---|---|---|---|
| Registration and login | 12 | 3 | 0 | 9 |
| Catalog and search | 13 | 9 | 4 | 0 |
| Cart | 10 | 7 | 2 | 1 |
| Checkout | 9 | 0 | 0 | 9 |
| Contact form | 7 | 4 | 2 | 1 |
| **Total** | **51** | **23** | **8** | **20** |

"Not run" cases need a registered test account and the payment form; they are written and ready for the next session. Failed cases are linked to the bug reports above; two catalog failures (unknown category page, no "no results" message) are recorded in the notes of BUG-002 and BUG-005.

## How the bugs were confirmed

- Every defect was reproduced on the live site, not taken from a known-issues list.
- Root causes were checked in Chrome DevTools: HTML attributes (`min="1"`, missing `required`, missing `enctype`), HTTP status codes and the URL that the search form builds.
- Screenshots are annotated in the page itself: a red frame marks the problem element and a yellow note explains the problem, the expected behaviour and the likely cause.

## Bug report template

Each report contains: ID, module, severity and priority, environment, related test cases, summary, preconditions, numbered steps, expected result, actual result, annotated screenshot, root-cause analysis or fix suggestion, and notes.

## Related portfolio projects

The same store is covered by automated test frameworks:

- [playwright-ecommerce-framework](https://github.com/s4ytv4n/playwright-ecommerce-framework): Playwright + TypeScript, UI + API tests, GitHub Actions ([report](https://s4ytv4n.github.io/playwright-ecommerce-framework/))
- [selenium-java-ecommerce-framework](https://github.com/s4ytv4n/selenium-java-ecommerce-framework): Selenium 4 + TestNG + REST Assured + Allure ([report](https://s4ytv4n.github.io/selenium-java-ecommerce-framework/))

## Note

automationexercise.com is a public practice site built for QA training. All test data uses disposable `example.com` addresses. No client or employer material is included in this repository.
