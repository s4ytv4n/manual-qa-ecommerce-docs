# Test Cases — Contact Us Form

Status legend: **Pass** · **Fail** · **Not run**

| ID | Title | Preconditions | Steps | Test data | Expected result | Priority | Status |
|---|---|---|---|---|---|---|---|
| TC-CNT-01 | Submit with all fields valid | — | 1. Open `/contact_us`<br>2. Fill Name, Email, Subject, Message<br>3. Click Submit, confirm OK | Test data on `example.com` | "Success! Your details have been submitted successfully." and Home button | P1 | Pass |
| TC-CNT-02 | Email is required | — | 1. Leave Email empty, fill the rest<br>2. Click Submit | — | Not submitted; required-field message | P1 | Pass |
| TC-CNT-03 | Invalid email | — | 1. Enter email without `@`<br>2. Click Submit | `abc` | Not submitted; email format message | P2 | Pass |
| TC-CNT-04 | Empty Name, Subject and Message | — | 1. Fill only Email<br>2. Click Submit, confirm OK | Email only | Not submitted; required-field messages for Name, Subject, Message | P2 | **Fail** → [BUG-003](../bug-reports/BUG-003-contact-form-empty-message.md) |
| TC-CNT-05 | Attachment is delivered | — | 1. Fill all fields<br>2. Choose a small `.txt` file<br>3. Submit | `qa-attachment-test.txt` | File content is sent in the request (`multipart/form-data`) | P2 | **Fail** → [BUG-004](../bug-reports/BUG-004-contact-form-attachment-not-sent.md) |
| TC-CNT-06 | Cancel confirmation | — | 1. Fill all fields<br>2. Click Submit, choose Cancel | — | Nothing is submitted; entered data stays in the form | P3 | Not run |
| TC-CNT-07 | Home button after success | TC-CNT-01 done | 1. Click Home | — | Home page opens | P3 | Pass |
