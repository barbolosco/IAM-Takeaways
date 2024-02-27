# OAuth 2.0 flows

**OAuth 2.0 Flow**

In the OAuth 2.0 flow, the process involves several steps to ensure secure access to resources. Here are some key concepts present in every flow type:

**Authorization Request:** The client application (e.g., your fitness tracker) initiates the process by sending an authorization request to the resource owner's identity provider (e.g., Google, Facebook). This request specifies the desired access permissions.

**User Consent:** The identity provider prompts the user (the resource owner) to grant or deny access. If approved, the user consents to the specific permissions requested.

**Authorization Grant:** Upon consent, the identity provider issues an authorization grant, a temporary token indicating the user's approval. This grant is often an authorization code.

**Access Token Exchange:** The client application exchanges the authorization grant for an access token, a time-limited credential to access the requested resources. This exchange typically involves the authorization server and the client authenticating themselves.

**Resource Access:** With the access token in hand, the client application can now make authorized requests to the resource server (e.g., the platform where the user's data resides). The resource server validates the access token and, if valid, grants access to the specified resources.



Based on preferences like security, convenience and speed 4 major types of flows were created.



Authorization code (front channel + back channel)

<figure><img src="https://docs.vmware.com/en/Single-Sign-On-for-VMware-Tanzu-Application-Service/1.14/sso/Images/images-oauth_auth_code.png" alt=""><figcaption></figcaption></figure>

• Implicit (front channel only)&#x20;

<figure><img src="https://docs.vmware.com/en/Single-Sign-On-for-VMware-Tanzu-Application-Service/1.14/sso/Images/images-oauth_implicit.png" alt=""><figcaption></figcaption></figure>

• Resource owner password credentials (back channel only)&#x20;

<figure><img src="https://docs.vmware.com/en/Single-Sign-On-for-VMware-Tanzu-Application-Service/1.14/sso/Images/images-oauth_password.png" alt=""><figcaption></figcaption></figure>

• Client credentials (back channel only)

<figure><img src="https://docs.vmware.com/en/Single-Sign-On-for-VMware-Tanzu-Application-Service/1.14/sso/Images/images-oauth_client_credentials.png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="181"></th><th width="300">+</th><th>-</th></tr></thead><tbody><tr><td>Authorization Code Flow</td><td>secure, widely supported, flexible</td><td>more complex, not ideal for mobile apps</td></tr><tr><td>Implicit Flow</td><td>simple, fast</td><td>less secure, limited server-side validation</td></tr><tr><td>Resource Owner Password Credentials Flow</td><td>simplest for the app, </td><td>highly insecure, too risky</td></tr><tr><td>Client Credentials Flow</td><td>machine to machine authorization</td><td>no user consent, limited scope required</td></tr></tbody></table>

All Oauth 2.0 flows:

*   Authorization Code

    1. The client initiates the flow and redirects the user to the authorization server
    2. User authenticates and grants permission
    3. Authorization server redirects user back to client with an authorization code
    4. The client exchanges the code for an access token
    5. Access token grants access to protected resources



    Implicit

    1. Client redirects user to authorization server
    2. User authenticates and grants permission
    3. Authorization server redirects user back to client with an access token
    4. Access token grants access to protected resources



    Resource Owner Password Credentials

    1. Client collects user's username and password
    2. Client sends username, password, client ID, and client secret to authorization server
    3. Authorization server validates credentials and issues an access token
    4. Access token grants access to protected resources



    Client Credentials

    1. Client sends its own credentials (client ID and client secret) to the authorization server
    2. Authorization server validates client credentials and issues an access token
    3. Access token grants access to protected resources
