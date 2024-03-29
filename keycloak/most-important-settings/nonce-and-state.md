# nonce and state

**Understanding Nonce and State Parameters**

* **Nonce (Number Use Once):**
  * A cryptographic value generated by your application.
  * Included in the authorization request sent to the OpenID Provider (OP).
  * Returned by the OP in the ID Token.
  * Ensures protection against replay attacks, where an intercepted authorization request is reused.
  * **Must be unique** for each authorization request.
  * **Should not** be guessable or predictable.
* **State:**
  * An opaque value generated by your application.
  * Included in the authorization request sent to the OP.
  * Returned by the OP verbatim in the redirect URI during the callback.
  * Helps prevent Cross-Site Request Forgery (CSRF) attacks by ensuring the authorization request originated from your application.
  * Can be used to store additional information (e.g., CSRF token) for state management.
  * **Should be unique** for each authorization request.
  * **Can be** reused across multiple requests, but this is generally not recommended for security reasons.

**Creating Nonce and State Parameters in JavaScript/Node.js**

Here's a code snippet demonstrating how to generate these parameters using the `crypto` module and a library like `uid` (or a similar library for generating unique identifiers):

```javascript
const crypto = require('crypto');
const uid = require('uid');

function generateNonce() {
  return crypto.randomBytes(16).toString('hex');
}

function generateState() {
  return uid(24); // Generate a random 24-character string
}
```

**Using Nonce and State in OIDC Flow (Authorization Code Flow Example):**

1. **Authorization Request:**
   * Generate a unique `nonce` and a unique `state`.
   *   Include them in the authorization request sent to the OP's authorization endpoint:

       ```javascript
       const authorizationUrl = client.authorizationUrl({
         scope: 'openid email profile', // Replace with desired scopes
         nonce: generatedNonce,
         state: generatedState,
         // Other parameters (e.g., redirect_uri, response_type)
       });

       // Redirect the user to the authorizationUrl
       ```
2. **Authorization Response:**
   * The OP redirects the user back to your application's redirect URI with query parameters, including the original `state` value.
   * The OP may also include the `nonce` value in the ID Token (depending on the OP's configuration).
3.  **Callback Handling:**

    * Extract the `state` parameter from the redirect URI.
    * Verify that the `state` value matches the one you sent in the authorization request (protects against CSRF).
    * If using ID Tokens, extract the `nonce` claim from the ID Token.
    * Verify that the `nonce` value matches the one you sent in the authorization request (protects against replay attacks).

    ```javascript
    app.get('/callback', async (req, res) => {
      const state = req.query.state;
      const code = req.query.code; // Assuming Authorization Code Flow

      // Verify state (CSRF protection)
      if (!state || state !== expectedState) {
        // Handle invalid state error
        return res.status(400).send('Invalid state');
      }

      // Exchange authorization code for tokens (implementation omitted)
      // ...

      if (idToken) { // If using ID Tokens and nonce is returned
        const nonce = idToken.getClaim('nonce');

        // Verify nonce (replay attack protection)
        if (!nonce || nonce !== expectedNonce) {
          // Handle invalid nonce error
          return res.status(400).send('Invalid nonce');
        }
      }

      // Successfully authenticated user, proceed with application logic
      // ...
    });
    ```

### So, what's the difference?

**Purpose:**

* **Nonce (Number Use Once):** Protects against replay attacks. It ensures the authorization request hasn't been intercepted and reused with a different application.
* **State:** Protects against Cross-Site Request Forgery (CSRF) attacks. It verifies that the authorization response originated from the intended application and not a malicious attacker.

**Verification:**

* **Nonce:** The nonce value is **returned by the OpenID Provider (OP) in the ID Token**. Your application verifies that this value matches the one it sent in the authorization request.
* **State:** The state value is **returned by the OP verbatim** in the redirect URI during the callback. Your application verifies that this value matches the one it originally sent.

**Reuse:**

* **Nonce:** Must be **unique** for each authorization request. Never reuse a nonce.
* **State:** Can be **reused** across multiple requests, but this is generally not recommended as it reduces the protection against CSRF attacks. It's better to generate a new state value for each request.

Here's an analogy to illustrate the difference:

* **Think of a nonce as a one-time pad** used for encryption. It's used once to secure a specific communication and discarded afterward.
* **Think of state as a session identifier** used to verify that a user session is legitimate. It can be reused for the same user session, but it doesn't guarantee the same level of security as a nonce.
