# Terminology

Main actors:

* Resource owner: The individual or entity who ultimately controls and authorizes access to their data.
* Client: The third-party application or service that requests access to the resource owner's data.
* Authorization server: The central authority responsible for verifying a client's legitimacy and issuing temporary access tokens to authorized clients.
* Resource server: The system where the actual data resides and is backed up.

Tokens and credentials:

* Access token: a short-lived digital key granted by the authorization server to the client for accessing specific resources on the resource server.
* Authorization grant: A temporary credential (usually an authorization code) that is exchanged for an access token after the owner of the resource has given their consent.
* Refresh token: Retrieving new access tokens without requiring the user to re-authorize.

Flows and concepts:

* Redirect URI: The endpoint to which the user is redirected after authorization, usually to the client's application.
* Scope: Specific permissions granted to the client in relation to the data they can access.
* Consent screen: The interface where the resource owner reviews and approves (or denies) the requested authorizations.
* Back Channel: A secure communication channel between the client and the server, often used for the exchange of sensitive data.
* Front channel: A less secure communication channel, typically used for user interactions such as viewing the consent screen.
* PKCE (Proof Key for Code Exchange): A mechanism in OAuth 2.0 that adds security by dynamically generating a secret that is used to obtain access tokens, improving protection against certain attacks.
* Identity provider: A system used for Single Sign-On (SSO) that allows users to authenticate across different applications using their existing credentials.

Key concepts:

* Delegation: The ability of applications to act on behalf of the resource owner by obtaining access tokens from the identity provider.
* Consent Framework: A mechanism that ensures transparency and user control by requiring explicit consent from the resource owner before access to their data is granted.

Other:

* WebAuthn: Web standard that allows users to securely authenticate to websites by using biometric sensors, USB security keys or built-in authenticators instead of passwords. It improves security and usability by reducing reliance on easily compromised passwords.
