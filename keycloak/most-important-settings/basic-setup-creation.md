# Basic setup creation

## Realm

1. **Access the Admin Console:**
   * Open your web browser and navigate to the Keycloak Admin Console URL, typically `http://localhost:8080/auth/admin`.
   * Log in with administrative credentials.
2. **Create a new realm:**
   * Click the "master" realm name in the top-left corner.
   * Select "Create Realm" from the menu.
3. **Configure the realm:**
   * **Realm name:** Enter a unique name for your realm (e.g., "myrealm").
   * **Display name:** Optional, provide a user-friendly name for the realm (e.g., "My Realm").
   * **Enabled:** Ensure the checkbox is ticked to enable the realm.
   * **Access type:** Choose the desired access type:
     * **Public:** Anyone can access the realm without prior registration.
     * **Private:** Only authenticated users can access the realm.
     * **Offline access allowed:** Enable offline token support for the realm.
   * **Login Theme:** Select the desired login theme (default theme is available).
   * **Email Themes:** Select the desired email themes for various notifications.
   * **Registration Email Template:** Optional, configure the email template sent to users during registration.
4. **Save the realm:**
   * Click the "Save" button.

## User

**In Keycloak Administration Console:**

* Access the Keycloak Management Console (e.g., `http://localhost:8080/admin`).
* Log in with administrator credentials.
* Navigate to the **Users** tab under the desired realm.
* Click **Add user**.
* Enter the user's **Username**, **First Name**, **Last Name**, and **Email Address**.
* Optionally, configure additional attributes like:
  * **Enabled:** Control user's ability to log in.
  * **Email Verified:** Set to `true` if email verification is used.
  * **Credentials:** Set or import a password, configure reset/activation email templates, and choose temporary/permanent password flags.
  * **Federated Identities:** Link user to social/external providers.
  * **Attributes:** Create custom attributes for user profiles.
  * **Required Actions:** Enforce password reset, email verification, or other actions.
* Click **Save**.

## Client

1. **Log in to the Keycloak Administration Console:**
   * Open your web browser and navigate to the Admin Console URL, typically `http://localhost:8080/admin`.
   * Enter your Keycloak administrator credentials and log in.
2. **Select the Realm:**
   * In the top-left corner of the Admin Console, click the realm name (e.g., `master`).
   * If you have multiple realms, choose the one where you want to create the client.
3. **Navigate to the Clients Section:**
   * In the left-hand navigation bar, click on **Clients**. This will display a list of existing clients in the selected realm.
4. **Create a New Client:**
   * Click the **Create** button in the top-right corner of the Clients page.
5. **Configure the Client Details:**
   * **Client ID:** Enter a unique and meaningful identifier for your client application. This ID will be used to reference the client when authenticating users.
   * **Client Protocol:** Choose the appropriate protocol(s) supported by your client. Common options include:
     * **OpenID Connect:** For web-based applications that need user authentication and access tokens.
     * **saml:** For Single Sign-On (SSO) with SAML-based applications.
     * **bearer-only:** For server-to-server communication using an access token.
   * **Access Type:** Select the level of access granted to the client based on its security requirements:
     * **confidential:** Client secrets are used for authentication, suitable for highly secure applications.
     * **public:** No client secrets are used, suitable for public-facing applications or browser-based clients.
   * **Root URL:** The base URL of your client application. Keycloak will use this URL when redirecting users after authentication.
   * **Valid Redirect URIs:** Specify all acceptable redirect URIs within your client application where Keycloak can send authentication responses.
   * **Web Origins:** (Optional) If using CORS (Cross-Origin Resource Sharing), list the allowed origins (URLs) from which your client can make requests.
6. **Optional Settings (based on your chosen client protocol and access type):**
   * **Client Secret:** (For confidential clients) Generate a strong and unique client secret to be used for authentication.
   * **Access Grant Types:** (For OpenID Connect clients) Select the grant types supported by your client (e.g., authorization code, client credentials). See [guide-to-flows.md](guide-to-flows.md "mention")
   * **Scope:** (For OpenID Connect clients) Define the claims (user information) that the client is authorized to access.
   * **SAML Settings:** (For SAML clients) Configure SAML-specific settings like entity ID, service provider name, and logout URL.
7. **Save and Close:**
   * Carefully review your settings and click the **Save** button.
   * You will be redirected to the Client Details page, which displays the newly created client configuration.

