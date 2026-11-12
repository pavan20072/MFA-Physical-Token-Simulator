# MFA Guard — Register Number + SMS OTP + MFA Token Prototype

## Authentication flow
1. User enters the registered 10-digit mobile number.
2. The application generates a 6-digit OTP.
3. The OTP is verified.
4. After OTP verification, the MFA-token field is unlocked.
5. User enters the current 6-digit MFA token.
6. Access is granted only when the OTP and MFA token are valid.

## Run
Extract the ZIP and open `index.html` in Chrome, Edge or Firefox.

## Local demo
Because this is a standalone browser prototype, it cannot actually send SMS messages by itself.
For testing, the generated OTP is displayed on the page as **DEMO OTP**.

The MFA token is generated locally and changes every 30 seconds.

## Production implementation
For a real application, do NOT generate or expose the OTP in frontend JavaScript.
Use a backend server and an SMS provider. The flow should be:

Frontend → Backend → SMS provider → User's phone
Frontend → Backend → Verify OTP
Frontend → Backend → Verify MFA token → Session/access token

The backend should store the OTP securely with a short expiry and rate-limit OTP requests and verification attempts.
