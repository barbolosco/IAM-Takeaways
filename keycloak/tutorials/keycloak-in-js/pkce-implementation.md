# PKCE implementation

### &#x20;PKCE key creation

```javascript
function base64urlencode(str) {
  return btoa(String.fromCharCode.apply(null, new Uint8Array(str)))
      .replace(/\+/g, '-').replace(/\//g, '_').replace(/=+$/, '');
}
async function  generatePKCEPair() {
  const code = Array.from(  
    window.crypto.getRandomValues(new Uint32Array(28)), 
    dec => ('0' + dec.toString(16)).substr(-2)
  ).join('');
  const challenge = base64urlencode(
    await window.crypto.subtle.digest('SHA-256', new TextEncoder().encode(code))
  );
  return {code, challenge};
}
generatePKCEPair().then((res) => {
  localStorage.setItem("challenge", res.challenge);
  localStorage.setItem("code", res.code);
  console.log(res);
})

```

The previous code illustrate the creation of the two keys that will be exchanged during the authorization code flow, breaking it down, first we generate a 56 character string from a Uint32Array(28) filled with random bytes, that will become our `code_verifier`.

```javascript
Array.from(window.crypto.getRandomValues(new Uint32Array(28)),
dec => ('0' + dec.toString(16)).substr(-2)).join('');
```

Then we pass the `code_verifier` in a `digest('SHA-256', new TextEncoder().encode(code))` function to obtain an hash of the code, that we will convert in base64 with the special characters substituted for the standard urlencoding.

We then, await for the hashing function to terminate and will get the result that are going to be saved in the `localStorage`to be later used during the PKCE verification.

```javascript
// we prepere the code_challenge previously generated
// to be send in the GET request to the Authorization Endpoint with the 
// code_challenge_method to tell the server that we are using PKCE SHA-256
  url.searchParams.set('code_challenge', localStorage.getItem("challenge"));
  url.searchParams.set('code_challenge_method', 'S256');

```

```javascript
// in the callback file the verification_conde is sent to let the server check 
// the user's legitimacy
urlencoded.append("code_verifier", localStorage.getItem("code"));
```
