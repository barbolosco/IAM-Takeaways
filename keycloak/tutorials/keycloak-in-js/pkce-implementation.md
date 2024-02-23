# PKCE implementation

### &#x20;PKCE creation

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
```

```javascript
// in the callback file the verification_conde is sent to let the server check 
// the user's legitimacy
urlencoded.append("code_verifier", localStorage.getItem("code"));
```
