# Authentication not working properly for valid users

This document tracks the context for Issue #1 and the planned validation steps.

## User story
- As a registered user, I want to sign in with valid credentials and maintain an active session so that I can access protected areas without unexpected errors or logouts.

## Acceptance criteria
- [ ] Given a registered user with correct email/password, when they submit the login form, then the API returns 200 within 2 seconds and the user is redirected to the dashboard.
- [ ] An access token/session is issued and persisted correctly (HttpOnly + Secure + SameSite=Lax if cookie-based), and the user remains authenticated after page refresh.
- [ ] With invalid credentials, the API returns 401 with a generic error message (no user enumeration).
- [ ] CSRF protection allows legitimate login requests that include a valid CSRF token and blocks requests with missing/invalid tokens.
- [ ] Access to a protected route without authentication redirects to the login page and does not expose protected content.
- [ ] Logout clears/revokes tokens or session, and protected routes are inaccessible afterward.
- [ ] If using refresh tokens, access tokens can be refreshed until expiry; compromised/rotated refresh tokens are rejected.
- [ ] Basic audit/log entries exist for login success and failure events.

## Notes
- This PR only adds documentation to scope and validate the fix. Follow-up commits/PRs can add tests and code changes.
