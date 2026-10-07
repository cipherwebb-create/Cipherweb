# Deployment

## Firebase
1. Create a Firebase project.
2. Enable Email/Password or your chosen provider. Remove anonymous auth in production.
3. Enable App Check and enforce it for supported products.
4. Create Firestore in production mode.
5. Deploy:
   `firebase deploy --only firestore:rules,firestore:indexes`
6. Set `superAdmin:true` as a Firebase custom claim only from a trusted server-side bootstrap process.
7. Require MFA for administrator accounts.

## Server
Deploy the Node app to Cloud Run, ECS, Render, Fly.io, or another TLS-enabled managed runtime.
Store service-account credentials in the platform secret manager.

Environment:
- FIREBASE_PROJECT_ID
- FIREBASE_CLIENT_EMAIL
- FIREBASE_PRIVATE_KEY
- CLIENT_ORIGIN
- ADMIN_IP_ALLOWLIST

Do not commit `.env`.

## Client
Run `npm run build` and deploy `dist/` to Firebase Hosting, Cloudflare Pages, Vercel, or similar.

## Admin
- Verify Firebase ID tokens server-side with revocation checks.
- Require the `superAdmin` custom claim.
- Require MFA/2FA.
- Enforce an admin IP allowlist or zero-trust gateway.
- Audit every BLOCK/UNBLOCK/DEACTIVATE action.
- Use a separate privileged admin account.

## E2E
The starter uses Web Crypto AES-GCM. For a mature multi-device system, use public-key identity/device keys and wrap per-conversation keys to approved participant devices. Rotate keys after membership changes and support device/session revocation.

## Compliance
Log IP/device/timestamp as privileged metadata. Keep it separate from E2E message plaintext. Define retention, legal-request access, and deletion policies with counsel before launch.
