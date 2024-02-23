# js flows

### authorization code flow

Initiating the call to the authorization endpoint\
This code snippet demonstrates how to initiate an authentication request to the authorization endpoint. Here, we're setting up the parameters required for the authentication process. The parameters include the response type, client ID, redirect URI, scope, state, nonce, and code challenge for [PKCE ](pkce-implementation.md)(Proof Key for Code Exchange) flow. By including all parameters directly in the URL, we simplify the process for demonstration purposes, showcasing the various parameters that can be passed to the endpoint.

```javascript
loginButton.addEventListener('click', async () => {
  const authUrl = 'http://localhost:8085/realms/test/protocol/openid-connect/auth';
  const clientId = 'pkce-test-client';
  const redirectUri = 'http://localhost/callback.html';
  const scope = 'openid profile';
  const state = "random"
  localStorage.setItem('clientId',clientId);
  // Build the authorization URL with parameters
  const url = new URL(authUrl);
  url.searchParams.set('response_type', 'code');
  url.searchParams.set('nonce', 'bkmnbgty78dfghytredsx');
  url.searchParams.set('client_id', clientId);
  url.searchParams.set('redirect_uri', redirectUri);
  url.searchParams.set('scope', scope);
  url.searchParams.set('state', state);
  url.searchParams.set('code_challenge', localStorage.getItem("challenge"));
  url.searchParams.set('code_challenge_method', 'S256');
  // Redirect the user to the authorization server
  window.location.href = url.toString();
});  
```

<table><thead><tr><th width="389">Capability config</th><th width="160"></th></tr></thead><tbody><tr><td>Client authentication</td><td>off</td></tr><tr><td>Standard flow</td><td>on</td></tr><tr><td>Implicit flow</td><td>off</td></tr><tr><td>Direct access grants</td><td>off</td></tr><tr><td>PKCE (S256)</td><td>on</td></tr></tbody></table>

```javascript
pkceTokenButton.addEventListener('click', async () => {
      const myHeaders = new Headers();
      myHeaders.append("content-type", "application/x-www-form-urlencoded");
 
      const urlencoded = new URLSearchParams();
      urlencoded.append("grant_type", "authorization_code");
      urlencoded.append("client_id", "pkce-test-client");
      urlencoded.append("redirect_uri", "http://localhost/callback.html");
      urlencoded.append("code", code);
      urlencoded.append("code_verifier", localStorage.getItem("code"));
      
      const requestOptions = {
        method: "POST",
        headers: myHeaders,
        body: urlencoded,
        redirect: "follow"
      };
      
      fetch("http://localhost:8085/realms/test/protocol/openid-connect/token", requestOptions)
        .then((response) => response.text())
        .then((result) => {
            console.log(JSON.stringify(JSON.parse(result), null, 2));
            const access_token = JSON.parse(atob((JSON.parse(result).access_token).split('.')[1]));
            console.log(JSON.stringify(access_token, null, 2));
            const id_token = JSON.parse(atob((JSON.parse(result).id_token).split('.')[1]));
            console.log(JSON.stringify(id_token, null, 2));
            
        })
        .catch((error) => {
            document.getElementById('callback').textContent = error;
        });

    });
```

### implicit code flow

```javascript
implicitLoginButton.addEventListener('click', async () => {
  // Replace with your authorization server and client details
  const authUrl = 'http://localhost:8085/realms/test/protocol/openid-connect/auth';
  const clientId = 'implicit-test-client';
  const redirectUri = 'http://localhost/callback.html';
  const scope = 'openid profile';
  const state = "random";
  const nonce = 'a4ndhGndhjzgjdna';
  // Build the authorization URL with parameters
  const url = new URL(authUrl);
  url.searchParams.set('response_type', 'id_token token');
  url.searchParams.set('client_id', clientId);
  url.searchParams.set('redirect_uri', redirectUri);
  url.searchParams.set('scope', scope);
  url.searchParams.set('state', state);
  url.searchParams.set('nonce', nonce);
  // Redirect the user to the authorization server
  window.location.href = url.toString();
});
```

<table><thead><tr><th width="389">Capability config</th><th width="160"></th></tr></thead><tbody><tr><td>Client authentication</td><td>off</td></tr><tr><td>Standard flow</td><td>off</td></tr><tr><td>Implicit flow</td><td>on</td></tr><tr><td>Direct access grants</td><td>off</td></tr><tr><td>PKCE (S256)</td><td>off</td></tr></tbody></table>

### Hybrid code flow

```javascript
hybridTokenLoginButton.addEventListener('click', async () => {
  // Replace with your authorization server and client details
  const authUrl = 'http://localhost:8085/realms/test/protocol/openid-connect/auth';
  const clientId = 'hybrid-test-client';
  const redirectUri = 'http://localhost/callback.html';
  const scope = 'openid profile';
  const state = "random";
  const type = 'code id_token';
  const nonce = 'a4ndhGndhjzgjdna';
  // Build the authorization URL with parameters
  const url = new URL(authUrl);
  url.searchParams.set('response_type', type);
  url.searchParams.set('client_id', clientId);
  url.searchParams.set('redirect_uri', redirectUri);
  url.searchParams.set('scope', scope);
  url.searchParams.set('state', state);
  url.searchParams.set('nonce', nonce);
  url.searchParams.set('code_challenge', localStorage.getItem("challenge"));
  url.searchParams.set('code_challenge_method', 'S256');
  // Redirect the user to the authorization server
  window.location.href = url.toString();
});

```

<table><thead><tr><th width="389">Capability config</th><th width="160"></th></tr></thead><tbody><tr><td>Client authentication</td><td>off</td></tr><tr><td>Standard flow</td><td>on</td></tr><tr><td>Implicit flow</td><td>on</td></tr><tr><td>Direct access grants</td><td>off</td></tr><tr><td>PKCE (S256)</td><td>on</td></tr></tbody></table>

```javascript
hybridPkceButton.addEventListener('click', async () => {
      const myHeaders = new Headers();
      myHeaders.append("content-type", "application/x-www-form-urlencoded");
 
      const urlencoded = new URLSearchParams();
      urlencoded.append("grant_type", "authorization_code");
      urlencoded.append("client_id", "hybrid-flow-client");
      urlencoded.append("redirect_uri", "http://localhost/callback.html");
      urlencoded.append("code", code);
      urlencoded.append("code_verifier", localStorage.getItem("code"));
      
      const requestOptions = {
        method: "POST",
        headers: myHeaders,
        body: urlencoded,
        redirect: "follow"
      };
      
      fetch("http://localhost:8085/realms/test/protocol/openid-connect/token", requestOptions)
        .then((response) => response.text())
        .then((result) => {
            //there is no id_token during code token flow
            console.log(JSON.stringify(JSON.parse(result), null, 2));
            const access_token = JSON.parse(atob((JSON.parse(result).access_token).split('.')[1]));
            console.log(JSON.stringify(access_token, null, 2));
        })
        .catch((error) => {
            document.getElementById('callback').textContent = error;
        });

    });
```
