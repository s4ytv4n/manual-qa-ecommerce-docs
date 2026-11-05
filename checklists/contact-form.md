# Checklist — Contact Us Form

Page: `/contact_us`

Result legend: ✅ Pass · ❌ Fail · ⏳ Not run yet

| # | Check | Result |
|---|---|---|
| 1 | Form shows Name, Email, Subject, Message, file upload and Submit | ✅ |
| 2 | Email is required | ✅ |
| 3 | Invalid email format is rejected | ✅ (browser validation) |
| 4 | Name, Subject and Message are required | ❌ [BUG-003](../bug-reports/BUG-003-contact-form-empty-message.md) |
| 5 | Submit asks for confirmation ("Press OK to proceed!") | ✅ |
| 6 | Cancel on the confirmation keeps entered data and does not submit | ⏳ |
| 7 | Success message "Success! Your details have been submitted successfully." is shown | ✅ |
| 8 | Attached file is actually sent to the server | ❌ [BUG-004](../bug-reports/BUG-004-contact-form-attachment-not-sent.md) |
| 9 | File type / size limits are enforced and communicated | ❌ No limits shown or enforced (see BUG-004 notes) |
| 10 | "Home" button after success returns to the home page | ✅ |
| 11 | Very long message (5000+ chars) is accepted or limited with a clear message | ⏳ |
| 12 | HTML / script in fields is not executed on the success page | ⏳ |
