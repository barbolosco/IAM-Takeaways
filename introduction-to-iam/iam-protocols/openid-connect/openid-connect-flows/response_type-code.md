# response\_type=code

Let's break down the "response\_type=code" flow of OIDC in the simplest terms:\
\


1. **User Interaction:** You, as a user, want to access a website or application that requires you to log in.
2. **Redirect to Authorization Server:** When you try to log in, the website or application redirects you to an authorization server. This server is like a gatekeeper that decides who gets access to what.
3. **Logging In:** At the authorization server, you log in with your username and password, just like you would on any website.
4. **Permission Granting:** After logging in, the authorization server asks you if you give permission for the website or application to access certain information about you, like your name or email.
5. **Authorization Code:** If you agree, the authorization server generates a special code (called an "authorization code") and sends it back to the website or application.
6. **Code Exchange:** The website or application takes this authorization code and sends it back to the authorization server, asking for an access token.
7. **Access Token:** The authorization server verifies the code and, if everything checks out, it sends back an access token. This access token acts like a key that lets the website or application access your information from the authorization server.
8. **Access Granted:** With this access token, the website or application can now access the information it needs from the authorization server, and you can use the website or application as intended.



<figure><img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*e3jR3GOzLTRJ8_oHrfW7aw.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*quwFs1fFCvTvLT80e_QHVA.png" alt=""><figcaption></figcaption></figure>
