# response\_type=code id\_token token

Here's the breakdown of the "response\_type=code id\_token token" flow of OIDC in straightforward terms:\


1. **User Interaction:** You wish to access a website or application that requires you to sign in or authenticate yourself.
2. **Redirect to Authorization Server:** When you attempt to log in, the website or app directs you to an authorization server, acting as a security checkpoint.
3. **Logging In:** At the authorization server, you provide your username and password to verify your identity.
4. **Permission Granting:** After successful login, the authorization server asks if you consent to the website or app accessing specific details about you, such as your name or email.
5. **Triple Response:** Instead of just one, you receive three tokens:
   * **Authorization Code:** This code is a special ticket that the website or app will use later to get an access token.
   * **ID Token:** This token contains information about you, like your name or email, allowing the website or app to personalize your experience.
   * **Access Token:** Similar to a backstage pass, this token grants access to your information stored on the authorization server.
6. **Access Granted:** Armed with these tokens, the website or app can now access your details securely and tailor its services accordingly.

<figure><img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*8RM_7DO3jVZlcLOo2nd9OQ.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*5AFIbZ3Il2kNuFmcAedNhA.png" alt=""><figcaption></figcaption></figure>
