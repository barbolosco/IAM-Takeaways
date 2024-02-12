# Authorization Code flow

The Authorization Code flow is widely used in OAuth 2.0 for web applications and provides a robust security mechanism. In this flow, the client initiates the authentication process by redirecting the user to the authorization server. The user then authenticates and grants permission for the client to access their resources. Upon successful authorization, the authorization server redirects the user back to the client with an authorization code. The client then exchanges this code for an access token, which it can use to access protected resources on behalf of the user. This flow ensures the security of user credentials as they are never exposed to the client, making it suitable for applications requiring a high level of security.

<figure><img src="https://blog.loginradius.com/static/709b8a5d49870d1186fa474732e74119/e5715/acf.png" alt=""><figcaption></figcaption></figure>
