Deploy the Firestore security rules included in `firestore.rules` to protect `api_keys`.

Quick deploy (Firebase CLI):

1. Install Firebase CLI and login:
   npm install -g firebase-tools
   firebase login

2. Initialize (if you haven't):
   firebase init firestore

3. Deploy rules:
   firebase deploy --only firestore:rules

Rules summary:
- Only authenticated users may create api_keys and must set owner == their uid.
- Only the owner may read/update/delete their api_keys.
- Creates must include the required fields: key, owner, created_at, created_at_ts, status, usage_count.

Notes:
- For production, generate API keys server-side and use the Admin SDK to create documents.
- Test rules using the Firebase Emulator (`firebase emulators:start --only firestore`) or the Rules Playground in the console.
