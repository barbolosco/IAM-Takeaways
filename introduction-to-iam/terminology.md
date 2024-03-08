# Terminology

Key players:

* **Resource Owner:** The individual or entity who ultimately controls and allows access to their data.
* **Client:** The third-party application or service seeking access to the resource owner's data.
* **Authorization Server:** The central authority responsible for verifying a client's legitimacy and issuing temporary access tokens to authorized clients.
* **Resource Server:** The system where the actual data resides and is secured.

Tokens and Credentials:

* **Access Token:** A short-lived digital key granted by the authorization server to the client for accessing specific resources on the resource server.
* **Authorization Grant:** A temporary credential (typically an authorization code) exchanged for an access token after the resource owner grants consent.
* **Refresh Token:** Obtain new access tokens without requiring the user to re-authorize.

Flows and concepts:

* **Redirect URI:** The endpoint where the user is redirected after authorization, typically to the client's application.
* **Scope:** Specific permissions granted to the client regarding the data they can access.
* **Consent Screen:** The interface where the resource owner reviews and approves (or denies) the requested permissions.
* **Back Channel:** A secure communication channel between the client and the server, often used for sensitive data exchange.
* **Front Channel:** A less secure communication channel, typically used for user interactions such as displaying the consent screen.
* **PKCE (Proof Key for Code Exchange):** A mechanism in OAuth 2.0 that adds security by dynamically generating a secret used for obtaining access tokens, enhancing protection against certain attacks.
* **Identity Provider:** A system used for Single Sign-On (SSO), allowing users to authenticate with their existing credentials across different applications.

Key Concepts:

* **Delegation:** The ability of applications to act on the resource owner's behalf by receiving access tokens from the identity provider.
* **Consent Framework:** A mechanism ensuring transparency and user control by requiring explicit consent from the resource owner before granting access to their data.

Other:

* WebAuthn:  web standard that allows users to securely authenticate to websites using biometric sensors, USB security keys, or built-in authenticators instead of passwords. It enhances security and user experience by reducing reliance on easily compromised passwords.
