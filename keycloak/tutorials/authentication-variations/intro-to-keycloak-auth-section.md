# Intro to keycloak auth section

The Keycloak Authentication section is where you can configure and manage different authentication flows. These flows define the steps a user must take to log in to your application. Keycloak comes with several built-in flows, and you can also create custom flows to meet your specific needs.

Here are the steps involved in a typical Keycloak authentication flow:

1. **The user attempts to access a protected application.** The application redirects the user to the Keycloak login page.
2. **The user enters their username and password.** Keycloak verifies the credentials against the user store.
3. **If the credentials are valid, Keycloak redirects the user back to the application.** The application grants the user access to the requested resources.

**Keycloak Authentication Flows**

Keycloak comes with several built-in authentication flows, including:

* **Browser Flow:** This is the most common flow, used for web-based applications.
* **Client Flow:** This flow is used for machine-to-machine authentication.
* **Direct Grant Flow:** This flow allows users to obtain access tokens directly from Keycloak.
* **Docker Flow:** This flow is used for authenticating Docker clients against Keycloak.
* **Registration Flow:** This flow allows users to register for new accounts.
* **Reset Credentials Flow:** This flow allows users to reset their passwords.

**Keycloak Browser Authentication Flow**

The Keycloak browser authentication flow is the most common flow used for web-based applications. It defines the steps a user must take to log in to your application using their username and password. Here are the steps involved in the Keycloak browser authentication flow, as shown in the image:

1. **Cookie**. Keycloak first checks if a valid session cookie exists. If a valid cookie is found, the user is already authenticated and is not required to enter their credentials again.
2. **Kerberos**. This option is disabled by default and can be skipped.
3. **Forms**. This is the most common subflow used in the browser flow. It consists of the following steps:
   * **Username Password Form**. This is a required step where the user enters their username and password.
   * **Browser-Conditional OTP**. This is an optional step that prompts the user for a one-time passcode (OTP) if multi-factor authentication (MFA) is enabled and required.

**Logic Behind the Browser Authentication Flow**

The logic behind the browser authentication flow is to verify the user's identity using their username and password, and optionally, an OTP. Here's a breakdown of the logic:

1. **Check for existing session**. Keycloak first checks if the user has a valid session cookie. If a valid cookie exists, it means the user has already been authenticated in this session and is not required to enter their credentials again. This step improves user experience by avoiding unnecessary login prompts.
2. **Username and password authentication**. If no valid cookie is found, Keycloak prompts the user for their username and password. Keycloak then verifies the entered credentials against the user store. If the credentials are valid, the flow proceeds to the next step.
3. **MFA (optional)**. If MFA is enabled and required for the user or the specific flow, Keycloak prompts the user for an OTP through the "Browser-Conditional OTP" step. If the entered OTP is valid, the authentication is successful.

**Customizing the Browser Authentication Flow**

While the image shows the default browser flow, you can customize this flow by adding or removing steps. For example, you might:

* **Add a social login step.** This would allow users to log in to your application using their social media credentials (e.g., Google, Facebook).
* **Add a challenge step.** This would require users to complete an additional challenge, such as answering a security question, before being granted access.
* **Add a consent step.** This would allow users to consent to the collection and use of their personal data before being granted access.

Practical guide

<figure><img src="../../../.gitbook/assets/gemini (3).png" alt=""><figcaption></figcaption></figure>

Here we have an example of a browser flow. The key elements to note in this image are as follows (from top to bottom):

* Inside the Bordeaux circle, you'll notice a green tick indicating that this flow is being used. In a client, only one version of a main type, such as a browser type, is employed.
* The vertical lines represent hierarchy, mostly chronological. This implies that if every option is set as "alternative," the user only needs to complete one choice to proceed within the web app.
* The green circles indicate a toggle, which is used solely to open other login possibilities, whether mandatory or optional, and serves a purely logical function.
* In a custom flow (created by you based on a copy of an original one like this), you may see more options. Notably, near the toggles, there's a pencil icon that allows you to add a "step" in the verification process from a selected list. You can also remove or rearrange all items on the screen to reorganize the user's login flow.

