# Test Cases — Registration and Login

Status legend: **Pass** · **Fail** · **Not run**

| ID | Title | Preconditions | Steps | Test data | Expected result | Priority | Status |
|---|---|---|---|---|---|---|---|
| TC-REG-01 | Register a new user with valid data | User is logged out; email not registered | 1. Open `/login`<br>2. Enter Name and Email under "New User Signup!"<br>3. Click Signup<br>4. Fill all required account and address fields<br>5. Click Create Account<br>6. Click Continue | Name: `QA Test`<br>Email: `qa.reg.{timestamp}@example.com`<br>Password: test password | "ACCOUNT CREATED!" is shown; after Continue the header shows "Logged in as QA Test" | P1 | Not run |
| TC-REG-02 | Signup with an already registered email | An account with the email exists | 1. Open `/login`<br>2. Enter Name and the existing Email<br>3. Click Signup | Existing email | Error "Email Address already exist!" is shown; user stays on `/login` | P1 | Not run |
| TC-REG-03 | Signup step 1 with empty fields | — | 1. Open `/login`<br>2. Leave Name and Email empty<br>3. Click Signup | — | Form is not submitted; browser shows required-field message | P2 | Pass |
| TC-REG-04 | Signup step 1 with invalid email | — | 1. Open `/login`<br>2. Enter Name and an email without `@`<br>3. Click Signup | Email: `abc` | Form is not submitted; message says the email must include `@` | P2 | Pass |
| TC-REG-05 | Required fields on account information form | Step 1 passed | 1. Leave Password, First name, Last name, Address, State, City, Zipcode, Mobile empty<br>2. Click Create Account | — | Account is not created; first empty required field is highlighted | P1 | Not run |
| TC-REG-06 | Invalid date of birth | Step 1 passed | 1. Select Day 31, Month February, any Year<br>2. Fill the rest with valid data<br>3. Click Create Account | DOB: 31 / February / 1990 | Date is rejected with a validation message | P3 | Not run |
| TC-LOG-01 | Login with valid credentials | Registered account exists; logged out | 1. Open `/login`<br>2. Enter email and password<br>3. Click Login | Valid account | Redirect to home page; header shows "Logged in as {name}" | P1 | Not run |
| TC-LOG-02 | Login with wrong password | Registered account exists | 1. Open `/login`<br>2. Enter valid email and wrong password<br>3. Click Login | Wrong password | Error "Your email or password is incorrect!"; user is not logged in | P1 | Not run |
| TC-LOG-03 | Login with unregistered email | — | 1. Open `/login`<br>2. Enter an unregistered email and any password<br>3. Click Login | `nobody.{timestamp}@example.com` | Same generic error as TC-LOG-02 (does not reveal whether the email exists) | P2 | Not run |
| TC-LOG-04 | Login form required fields | — | 1. Open `/login`<br>2. Click Login with empty fields | — | Form is not submitted; browser required-field message | P2 | Pass |
| TC-LOG-05 | Logout | User is logged in | 1. Click Logout | — | Redirect to `/login`; "Logged in as", "Logout" and "Delete Account" are no longer shown | P1 | Not run |
| TC-LOG-06 | Delete account | User is logged in with a disposable account | 1. Click Delete Account<br>2. Click Continue<br>3. Try to log in with the same credentials | — | "ACCOUNT DELETED!" is shown; login afterwards fails with the generic error | P2 | Not run |
