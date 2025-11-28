# Version 4.0 - Google Auth OTP & Welcome Emails

## New Features

### 1. Google Authentication with OTP
- **Enhanced Security:** Google Sign-In now requires an additional One-Time Password (OTP) verification step.
- **Flow:**
    1. User clicks "Sign in with Google".
    2. Google authenticates the user.
    3. Server generates a 6-digit OTP and sends it to the user's Google email.
    4. User is redirected to a new **Verify Login** page (`google-otp.html`).
    5. Upon successful OTP verification:
        - **Existing Users:** Logged in immediately.
        - **New Users:** Redirected to **Complete Profile** page (`google-complete.html`) to choose a username and optional phone number.
- **User Status:** New users created via Google Auth are initially marked as `isVerified: false` in the database, as per requirements.

### 2. Welcome Emails
- **Automated Emails:** A welcome email is sent to users upon:
    - Successful email verification (for local signups).
    - Account creation via Google Auth.
- **Design:** Emails feature a responsive, modern design with a gradient header.

### 3. Backend Improvements
- **OTP Endpoints:** Added `/api/auth/otp/request` and `/api/auth/otp/verify` endpoints (currently unused by frontend but available for future use).
- **Google Strategy:** Improved handling of existing users and email extraction from Google Profiles.
- **Bug Fixes:** Resolved an issue where existing users logging in via Google might encounter a "no email" error.

## Changes

- **Login Page:** Removed the "Login with OTP" button and modals from `login.html` to streamline the interface, focusing on Password and Google Login.
- **Database:** `User` model now supports `otpCode` and `otpExpires` fields.

## Files Added/Modified
- `server.js`: Updated auth logic, added OTP routes, configured email sending.
- `login.html`: Removed OTP UI elements.
- `google-otp.html`: New page for OTP entry.
- `google-complete.html`: New page for profile completion.
- `models/User.js`: Verified schema support for OTP fields.
