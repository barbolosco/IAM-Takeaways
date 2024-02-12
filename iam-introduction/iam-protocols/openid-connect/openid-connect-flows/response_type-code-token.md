# response\_type=code token

Let's see the explanation of the "response\_type=code token" flow of OIDC:\


1. **User Interaction:** You want to use a website or app that requires you to log in.
2. **Redirect to Authorization Server:** When you try to log in, the website or app sends you to an authorization server, which checks if you're allowed to access the site.
3. **Logging In:** At the authorization server, you enter your username and password to prove your identity.
4. **Permission Granting:** After logging in, the authorization server asks if it's okay for the website or app to access certain information about you, like your name or email.
5. **Authorization Code:** If you agree, instead of immediately giving access, the authorization server gives the website or app a special code (authorization code) and sends you back to the site.
6. **Access Token Exchange:** The website or app then takes this authorization code and asks the authorization server for an access token.
7. **Access Token Received:** If everything checks out, the authorization server sends back an access token along with the authorization code.
8. **Access Granted:** Now armed with both the authorization code and access token, the website or app can securely access your information and provide you with the services you requested.

<figure><img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*lVCDaW-saARFbXWvrqDNrg.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*3j8ru4u7PkfX9W4PF3zUGw.png" alt=""><figcaption></figcaption></figure>
