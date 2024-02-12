# response\_type=id\_token token

Here's a straightforward explanation of the "response\_type=id\_token token" flow of OIDC:

1. **User Interaction:** You aim to use a website or application that requires you to log in or authenticate yourself.
2. **Redirect to Authorization Server:** When you attempt to log in, the website or application redirects you to an authorization server, acting as a gatekeeper.
3. **Logging In:** At the authorization server, you provide your username and password to confirm your identity.
4. **Permission Granting:** Following successful login, the authorization server asks if you consent to the website or application accessing specific details about you, such as your name or email address.
5. **ID Token and Access Token:** Instead of obtaining only an access token, as in the "response\_type=token" flow, here you receive both an ID token and an access token.
6. **Access Granted:** With the ID token, the website or application gains access to basic user information, such as your name and email. Simultaneously, the access token serves as a key to access more detailed information or protected resources.

<figure><img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*EDlE_l7EniylAkBFXXQqwA.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*JG9-HtT_e5-yER5hG2bXOQ.png" alt=""><figcaption></figcaption></figure>
