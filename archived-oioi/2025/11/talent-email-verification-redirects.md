---
description: >-
  A report for a small glitch around the email account verification flow that leads to a 404 page, even though the URL indicates a successful verification.
icon: markdown
cover: ../../../.gitbook/assets/GnqSSpvagAAr5vT.jpeg
coverY: 0
---

# Email verification success redirects to 404 page (login-callback) and second-click shows invalid/expired token

> Hi Talent Protocol team,
>
> I’d like to report a small glitch around the email account verification flow that leads to a 404 page, even though the URL indicates a successful verification. The behavior on a second click of the same verification link can also be confusing (invalid/expired token).

---

## 1. Context

- Account: Prof. NOTA / endhonesa (Talent Plus)
- Location: Jakarta, Indonesia
- Observed: 3 December 2025
- Platform: Desktop, macOS 10.15.7
- Browser: Chrome 142
- Session: Logged in on talentprotocol.com when starting the flow

---

## 2. Steps to reproduce

1. Log in to your account on `https://talentprotocol.com`.
2. Go to **Settings → Security**:  
   `https://talentprotocol.com/~/settings/security`
3. Under the email section, submit an email address to verify.
4. Open the verification email that is sent to that address.
5. Click the verification link in the email, which looks like:  
   `https://api.talentprotocol.com/verify_email_account/<token>`
6. The browser is then redirected to a URL like:  
   `https://talent.app/login-callback?success_message=Email%20account%20verified%20successfully!`
   but the page shown is a **“404 – Not Found”** page.
7. Go back to `https://talentprotocol.com/~/settings/security` and reload the page.  
   - The email status now appears as **verified**, which suggests that the verification actually worked server-side.
8. From the same verification email, click the **same verification link again**.  
   - This time, the link reports that the token is **invalid or expired** (as expected for a one-time token), which can further confuse a user who just saw a 404 previously.

---

## 3. Actual behavior

- On the **first click**:
  - The verification endpoint redirects to  
    `https://talent.app/login-callback?success_message=Email%20account%20verified%20successfully!`
  - The page content at that URL shows **“404 – Not Found”**, even though the query string carries a success message.
  - Despite the 404, refreshing the Security settings page on `talentprotocol.com` shows that the email **is** verified.

- On a **second click** of the same verification link:
  - The token is now considered **invalid or expired** (as expected for a one-time verification link),
  - So the user’s second attempt to “make sure it worked” also results in an error state.

From the user’s point of view, the sequence looks like:

1. Click verification link → 404 page.  
2. Try again (natural reaction) → token invalid/expired.  

Even though the email ends up verified, the visual flow feels like something went wrong twice.

---

## 4. Expected behavior

For a better UX, I’d expect one of the following:

1. **A dedicated success page** for the `login-callback` route on `talent.app` that:
   - Reads the `success_message` (and/or `error_message`) query parameters, and
   - Displays a clear message such as:  
     > “Email account verified successfully. You can now continue using Talent.”

   If a one-time token is clicked again, the page could:
   - Show a friendly message like:  
     > “This verification link has already been used. Your email is already verified.”  
     instead of a generic error or 404.

2. **Or a redirect back to the main app** (for example to `https://talentprotocol.com/~/settings/security` or the main profile page) with:
   - A banner/toast indicating that the email account was verified successfully on the first click,
   - And, on subsequent clicks, a message explaining that the link has already been used.

In both cases, the user should always see a **clear, non-error message** after interacting with a valid verification link, whether it’s the first or a repeated click.

---

## 5. Impact

- Functionally, the email verification **does succeed** on the first click:
  - Reloading the Security page shows the email as verified.
- However, from the user’s perspective the flow feels broken:

  - First click:
    - They land on a 404 page after doing exactly what the email tells them to do.
    - This creates doubt about whether the verification actually worked.
  - Natural reaction:
    - They go back to the email and click the link again, hoping it will “work this time”.
  - Second click:
    - They are told the token is invalid or expired, which reinforces the feeling that something went wrong, even though their email is already verified.

- Because this is a **security-sensitive step** (email verification), the combination of:
  - a 404 page,
  - followed by an invalid/expired token message,
  can easily undermine trust and cause unnecessary support requests or repeated attempts.

Fixing this will make the verification step feel aligned with the underlying success state, rather than at odds with it.

---

## 6. Suggestions

Some possible fixes:

- Implement a proper `login-callback` route on `talent.app` that:
  - Handles `success_message` and `error_message` query params,
  - Renders a simple confirmation UI for successful verification,
  - Detects when a verification link has already been used and displays a clear “already verified” message instead of a generic error.

- Alternatively, have `verify_email_account` redirect directly back to:
  - A known in-app route on `talentprotocol.com` (e.g. Security settings),
  - With a toast/snackbar summarizing the result:
    - First click: “Email account verified successfully.”
    - Second click onward: “This verification link has already been used; your email is already verified.”

Even a minimal, non-404 message would significantly improve the experience.

---

## 7. Happy to help more

I’m very happy to keep reporting small glitches like this as a regular user of Talent Protocol and Talent App.

If this level of QA is useful, I’d also be interested in:

- Testing auth & identity flows (email, wallet, ENS/Basename) before changes go live,
- Opening detailed issues or documentation PRs for these edge cases,
- Providing structured feedback on UX around security and verification.

Please let me know:

- If there’s a preferred channel where you’d like issues like this reported (GitHub, Discord, or a specific form), and
- If there are any QA / docs contribution paths where someone like me could be listed as a contributor.

Thanks a lot for your work on Talent Protocol — and for looking into this small but important detail in the verification flow.

Reported by,  
**Prof. NOTA** (on [Farcaster](https://farcaster.xyz/myreceipt) / [X](https://x.com/MyReceiptTT))

---

P.S. Read this document freely for information and guidance. Do not redistribute or restate—no quotes, summaries, paraphrases, or derivatives—without prior written permission from [**Prof. NOTA**](https://nota.endhonesa.com/). Sharing the link is allowed. So, share the link, not the text. Do not discuss or re-tell the contents in any form—written, spoken, or recorded—without prior written permission.

---
