# Keycloak in js

## Keycloak integration methods

Keycloak can be integrated into JavaScript (or its frameworks like Spring Boot) either through an adapter or by manually calling the server's endpoints using vanilla JavaScript. All [OIDC flows](../../../iam-introduction/iam-protocols/openid-connect/openid-connect-flows/) involve the client requesting access from the server's authorization endpoint. Implementing these calls to the endpoints is simpler with the adapter, but this approach hides the calls within the final script. In other words, you cannot see how the raw calls are made or where they occur.&#x20;

```html
<script src="http://localhost:8085/js/keycloak.js"></script>
```

<pre class="language-javascript"><code class="lang-javascript"><strong>// example of call with js adapter
</strong><strong>window.keycloak.init({
</strong>  clientId: 'web-app1',
  realm: 'your_realm',
  authServerUrl: 'http://localhost:8080/auth',
  flow: 'standard',
  responseType: 'code',
  codeChallenge: code_challenge,
  codeChallengeMethod: 'S256',
  onLoad: 'check-sso',
  pkceMethod: 'S256'
});
</code></pre>

Now, I'll provide an example of calling an authorization endpoint and a token endpoint, focusing on [all possible parameters](../../../iam-introduction/iam-protocols/openid-connect/parameters-walk-trough.md) for each call and how they are configured. We'll delve into where to correctly place each parameter for different flow types in the subsequent "flows" section. To access a Keycloak cheat sheet listing accepted OIDC flow parameters, visit `http://{host}:{port}/realms/{realm}/.well-known/openid-configuration` while Keycloak is running.

### Authorization an token endpoint calls

In this examples, we're initiating the initial call to the authorization and token endpoints. Currently, we're including all parameters directly in the URL for demonstration purposes, without focusing on specific flows. This approach allows us to showcase the variety of parameters that can be passed to the endpoint. While in a real-world scenario, parameters might be handled differently based on the specific OIDC flow being utilized.

```javascript
LoginButton.addEventListener('click', async () => {
  const url = new URL(authUrl);
  url.searchParams.set('response_mode', mode);
  url.searchParams.set('response_type', type);
  url.searchParams.set('client_id', clientId);
  url.searchParams.set('redirect_uri', redirectUri);
  url.searchParams.set('scope', scope);
  url.searchParams.set('state', state);  
  url.searchParams.set('code_challenge', code);
  url.searchParams.set('nonce', nonce);
  url.searchParams.set('code_challenge_method', Cmethod);
  url.searchParams.set('prompt', 'login consent');
  url.searchParams.set('max_age', '3600');
  url.searchParams.set('ui_locales', 'en');
  url.searchParams.set('acr_values', 'acr_example');
  url.searchParams.set('claims', 'email verified');

  window.location.href = url.toString();
});
```

```javascript
tokenButton.addEventListener('click', async () => {
    const myHeaders = new Headers();
    myHeaders.append("content-type", "application/x-www-form-urlencoded");

    const urlencoded = new URLSearchParams();
    urlencoded.append("grant_type", "authorization_code");
    urlencoded.append("client_id", "hybrid-flow-client");
    urlencoded.append("redirect_uri", "http://localhost/callback.html");
    urlencoded.append("code", code;
    urlencoded.append("code_verifier", "gyujnbvgfrtyu";
    urlencoded.append("scope", "openid profile email");
    urlencoded.append("nonce", "random_nonce_value");
    urlencoded.append("client_secret", "your_client_secret");

    const requestOptions = {
      method: "POST",
      headers: myHeaders,
      body: urlencoded,
      redirect: "follow"
    };
    
    fetch("http://localhost:8085/realms/test/protocol/openid-connect/token", requestOptions)
      .then((response) => response.text())
      .then((result) => {
         //manage and elaborate results
      })
      .catch((error) => {
          document.getElementById('callback').textContent = error;
      });
});
```



























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
