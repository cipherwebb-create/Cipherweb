# Security checklist

- Firestore deny-by-default rules.
- Firebase App Check.
- Helmet + strict CSP.
- CORS allowlist, not `*`.
- Rate limits on auth, search, friend requests, group joins, messaging, and admin APIs.
- Server-side Firebase token verification.
- Zod validation on all request bodies/query/path parameters.
- bcrypt/Argon2 only for passwords that are actually owned by the application. Firebase Auth normally owns password hashing, so do not double-hash Firebase passwords.
- 2FA/MFA for administrators.
- Admin IP allowlist.
- Audit logs for privileged actions.
- Secret manager and key rotation.
- Dependency scanning.
- HSTS at the edge.
- Never put Firebase Admin credentials in the browser.
- Never trust a client-supplied UID in Socket.IO; verify the Firebase ID token.
- Never claim that browser code can prevent screenshots or OS-level copying.
