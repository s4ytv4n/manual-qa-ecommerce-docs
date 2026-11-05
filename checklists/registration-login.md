# Checklist — Registration and Login

Page: `/login` (Login form and New User Signup form), `/signup` (account details)

Result legend: ✅ Pass · ❌ Fail · ⏳ Not run yet

## Signup (step 1: name + email)

| # | Check | Result |
|---|---|---|
| 1 | "New User Signup!" form shows Name, Email and Signup button | ✅ |
| 2 | Name and Email are required (browser validation on empty submit) | ✅ |
| 3 | Email field rejects values without `@` | ✅ |
| 4 | Already registered email shows "Email Address already exist!" | ⏳ |
| 5 | Valid name + new email opens the "Enter Account Information" form | ⏳ |
| 6 | Name and email from step 1 are pre-filled on step 2 | ⏳ |

## Signup (step 2: account information)

| # | Check | Result |
|---|---|---|
| 7 | Title radio buttons (Mr / Mrs) are selectable, only one at a time | ⏳ |
| 8 | Password is masked | ⏳ |
| 9 | Date of birth dropdowns contain valid ranges (days 1–31, 12 months, years) | ⏳ |
| 10 | Invalid date combination (e.g. 31 February) is rejected | ⏳ |
| 11 | Newsletter and special offers checkboxes can be toggled | ⏳ |
| 12 | Required address fields (First name, Last name, Address, Country, State, City, Zipcode, Mobile) block submit when empty | ⏳ |
| 13 | Country dropdown lists all supported countries | ⏳ |
| 14 | Zipcode and Mobile accept only valid formats | ⏳ |
| 15 | "Create Account" shows "ACCOUNT CREATED!" and Continue logs the user in | ⏳ |
| 16 | Header shows "Logged in as {name}" after registration | ⏳ |

## Login / logout / delete

| # | Check | Result |
|---|---|---|
| 17 | Login form shows Email, Password and Login button | ✅ |
| 18 | Email and Password are required | ✅ |
| 19 | Valid credentials log the user in; header shows "Logged in as {name}" | ⏳ |
| 20 | Wrong password shows "Your email or password is incorrect!" | ⏳ |
| 21 | Unknown email shows the same generic error (no account enumeration) | ⏳ |
| 22 | Email is case-insensitive at login | ⏳ |
| 23 | Logout returns to `/login` and hides account links | ⏳ |
| 24 | After logout, browser Back does not restore a logged-in session | ⏳ |
| 25 | Delete Account shows "ACCOUNT DELETED!" and the account can no longer log in | ⏳ |
