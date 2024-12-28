# Firebase onAuthStateChanged Inconsistency with Session Expiration

This repository demonstrates a bug where the Firebase `onAuthStateChanged` listener fails to reliably detect session expiration, potentially leading to inconsistencies in the application's UI and functionality.  The example uses JavaScript, but the problem is relevant to other Firebase SDKs.

## Bug Description
The issue arises when a Firebase user's session expires or is invalidated (e.g., password reset, account deletion).  The `onAuthStateChanged` listener doesn't always trigger the expected state change, resulting in the UI maintaining the logged-in state even though authentication requests fail.

## Reproduction Steps
1. Clone this repository.
2. Install dependencies: `npm install`.
3. Configure your Firebase project.
4. Run the application.
5. Observe the UI behavior before and after session invalidation (e.g., manually sign out from Firebase console).

## Solution
The solution implemented here involves a more robust approach for checking the session's validity, going beyond the `onAuthStateChanged` listener.  It utilizes a combination of a periodic check to verify the ID token and appropriate handling of invalid tokens.

## License
MIT