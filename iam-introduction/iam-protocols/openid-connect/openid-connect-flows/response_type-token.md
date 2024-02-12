# response\_type=token

Let's see how the "response\_type=token" functions:\


1. **User Interaction:** You want to access a website or app that requires you to log in or authenticate yourself.
2. **Redirect to Authorization Server:** When you try to log in, the website or app sends you to an authorization server. Think of it like a security checkpoint.
3. **Logging In:** At the authorization server, you enter your username and password to prove who you are.
4. **Permission Granting:** After logging in, the authorization server asks if you're okay with the website or app accessing certain details about you, like your name or email address.
5. **Access Token Directly:** Instead of getting an authorization code first, the authorization server immediately gives the website or app an access token. This token acts as a key to access your information.
6. **Access Granted:** With this access token, the website or app can now access the information it needs from the authorization server without needing to exchange anything else.\


<figure><img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*uWXvy16bG-ClFLeEtdXnUw.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*kNt-5dQ5GjNPNgl98QmVkg.png" alt=""><figcaption></figcaption></figure>
