# response\_type=code id\_token

Here's the explanation of the "response\_type=code id\_token" flow of OIDC in a straightforward manner:\


1. **User Interaction:** You aim to access a website or application that requires you to log in or authenticate.
2. **Redirect to Authorization Server:** When you attempt to log in, the website or application redirects you to an authorization server, which acts as a security checkpoint.
3. **Logging In:** At the authorization server, you provide your username and password to verify your identity.
4. **Permission Granting:** Upon successful login, the authorization server asks if you permit the website or application to access specific information about you, such as your name or email address.
5. **Authorization Code and ID Token:** Instead of just receiving an access token or only an ID token, in this flow, you receive both an authorization code and an ID token.
6. **Code Exchange:** The website or application takes the authorization code received and sends it back to the authorization server to request an access token.
7. **Access Token Issuance:** The authorization server validates the authorization code and issues an access token. Additionally, it sends the ID token back to the website or application.
8. **Access Granted:** With the access token and ID token, the website or application can now access the required information about you from the authorization server, allowing you to use the website or application as intended.\


<figure><img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*yAzZvVzy6A3nHvyfTfrsHA.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*d7mevOoOEMhePjo3TkORlw.png" alt=""><figcaption></figcaption></figure>
