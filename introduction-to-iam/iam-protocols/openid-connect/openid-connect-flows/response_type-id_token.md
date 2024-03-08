# response\_type=id\_token

Here's a explanation of the "response\_type=id\_token" flow of OIDC in simple terms:

1. **User Interaction:** You wish to log in to a website or app that requires authentication.
2. **Redirect to Authorization Server:** When you attempt to log in, the website or app redirects you to an authorization server, which acts like a gatekeeper.
3. **Logging In:** At the authorization server, you provide your username and password to prove your identity.
4. **Permission Granting:** After successfully logging in, the authorization server asks if you consent to the website or app accessing certain information about you, such as your name or email.
5. **ID Token Issuance:** Instead of providing an access token or an authorization code, the authorization server immediately issues an ID token containing your identity information.
6. **Access Granted:** With the ID token, the website or app can verify your identity and provide you with access to its features or services.

<figure><img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*1kNnTe0Eqf7S_IOUcT-ftg.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*95aX-M20iBFGB08q_Yep2w.png" alt=""><figcaption></figcaption></figure>
