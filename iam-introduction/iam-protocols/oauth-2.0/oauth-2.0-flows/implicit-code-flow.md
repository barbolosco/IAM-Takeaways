# implicit code flow

The Implicit flow is primarily designed for single-page web applications where the client is unable to securely store client secrets. In this flow, the client initiates the authentication process similarly to the Authorization Code flow, redirecting the user to the authorization server. After the user authenticates and grants permission, the authorization server redirects the user back to the client with an access token directly, without an intermediate authorization code exchange. While this flow simplifies the process by eliminating the need for a code exchange, it is considered less secure due to the potential exposure of access tokens in the browser.

<figure><img src="https://iq.opengenus.org/content/images/2020/04/implicit-grant-flow-1.png" alt=""><figcaption></figcaption></figure>
