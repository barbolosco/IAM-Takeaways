# Keycloak in js

## Client side

### Include the Keycloak JavaScript library in your HTML:

```html
<script src="http://localhost:8085/js/keycloak.js"></script>
```

### Establish a connection with the authentication endpoint, typically in your `index.html` file.&#x20;

Here's an example configuration:

```javascript
javascriptCopy codewindow.keycloak.init({
  clientId: 'web-app1',
  realm: 'your_realm',
  authServerUrl: 'http://localhost:8080/auth',
  flow: 'standard',
  responseType: 'code',
  codeChallenge: code_challenge,
  codeChallengeMethod: 'S256',
  onLoad: 'check-sso',
  pkceMethod: 'S256'
});
```

Configuration Options:

* `clientId`: Unique identifier for your application in Keycloak.
* `realm`: Realm where your application is defined.
* `authServerUrl`: Base URL of the Keycloak authentication server.
* `flow`: Authentication flow to use (e.g., 'standard', 'implicit').
* `responseType`: Expected response type from Keycloak (e.g., 'code', 'token').
* `codeChallenge`: Code challenge generated for PKCE (Proof Key for Code Exchange).
* `codeChallengeMethod`: Hashing method used for the code challenge.
* `onLoad`: Action to take on page load (e.g., 'check-sso', 'login-required').
* `pkceMethod`: PKCE method to use ('S256' is recommended).

### Establish a connection with the token endpoint, typically in your `callback.html` file.

Here's an example configuration:

```javascript
fetch('http://localhost:8085/realms/test/protocol/openid-connect/token', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/x-www-form-urlencoded',
        'Origin': 'http://callback.html'
      },
      body: new URLSearchParams({
        grant_type: 'authorization_code',
        code: code,
        client_id: 'pkce-test-client', 
        redirect_uri: 'http://localhost/callback.html', 
        code_verifier: codeVerifier
      })
    })
```

## Server side

it is necessary to create a realm, client and user \
the most important settings are folw settings\
