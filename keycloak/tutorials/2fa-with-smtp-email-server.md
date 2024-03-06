# 2FA with SMTP email server

### Configuring Keycloak for Email Login and SMTP (Without a Domain)

This guide outlines the steps to configure Keycloak for email login and SMTP server connection using Gmail (without requiring a purchased domain). However, **be aware of the security implications of using Less Secure App Access** in Gmail, as described in Option 1 of the previous guide.

**Prerequisites:**

* A Keycloak server running.
* A Gmail account with 2FA enabled (**Option 1**: Less Secure App Access **enabled** temporarily).
* An app password generated from your Gmail account (**Option 1** only).

**Steps:**

1.

    **Steps:**

    1. **Enable Login with Email:**
       * Log in to your Keycloak server's administration console.
       * Select the realm for which you want to enable email login.
       * Navigate to the "Login" tab in the realm settings.
       * Under "Broker Login," click on "Add identity provider."
       * Select "Email" as the provider type.
       * Enable the "Login with Email" toggle.
       * In the "Link Email to User Federation Provider" dropdown, select "Create new..."
       * Choose a name for the provider (e.g., "Email User Federation") and select "Empty" as the mapper type.
       * Click "Save."
    2. **Configure Email Tab:**
       * Navigate to the "Email" tab in the realm settings.
       * Configure the following settings:
         * **SMTP Server:** Enter the details based on your chosen option:
           * **Option 1 (Less Secure App Access, Not Recommended):** `smtp.gmail.com`
           * **Option 2 (Dedicated ESP, Recommended):** Use the server address provided by your ESP.
         * **SMTP Port:**
           * **Option 1:** `587`
           * **Option 2:** Use the port number provided by your ESP.
         * **TLS Security:**
           * **Option 1:** `STARTTLS`
           * **Option 2:** Follow your ESP's recommendations.
         * **From:** A desired sender email address (even without a domain, e.g., `no-domain@keycloak.com`).
         * **Username:**
           * **Option 1:** Your **full Gmail address** (e.g., `your_username@gmail.com`).
           * **Option 2:** Username provided by your ESP.
         * **Password:**
           * **Option 1:** The **16-character app password** generated in step 1 of the previous guide.
           * **Option 2:** Password provided by your ESP.
       * Click "Save."

**Option 1: Using Gmail SMTP with Less Secure App Access (Not Recommended):**

1. Follow the steps in the previous guide (**Option 1**) to enable Less Secure App Access in your Gmail account and create an app password.
2. Navigate to the "Email" tab in the realm settings.
3. Configure the following settings:
   * **SMTP Server:** `smtp.gmail.com`
   * **SMTP Port:** `587`
   * **TLS Security:** `STARTTLS`
   * **From:** A desired sender email address (even without a domain, e.g., `no-domain@keycloak.com`).
   * **Username:** Your **full Gmail address** (e.g., `your_username@gmail.com`).
   * **Password:** The **16-character app password** generated in step 1.
4. Click "Save."

**Option 2: Using a Dedicated ESP (Recommended):**

1. Sign up for a dedicated ESP and obtain their SMTP server details, port number, and authentication credentials.
2. Navigate to the "Email" tab in the realm settings.
3. Configure the settings provided by your ESP, including:
   * **SMTP Server:** Address provided by your ESP.
   * **SMTP Port:** Port number provided by your ESP.
   * **TLS Security:** Follow your ESP's recommendations.
   * **From:** A desired sender email address.
   * **Username:** Username provided by your ESP.
   * **Password:** Password provided by your ESP.
4. Click "Save."
5. **Test Email Sending (Optional):**
   * In the "Users" tab, select a user.
   * Click on the "Credentials" tab and then "Reset Password."
   * Enter a new password for the user and click "Reset Password."
   * Check your email inbox (including spam folders) for a password reset email from Keycloak. If you receive the email, the configuration is successful.

**Remember:**

* **Option 1 (using Less Secure App Access) is strongly discouraged** due to the security risks involved.
* **Option 2 (using a dedicated ESP) is highly recommended** for enhanced security and email deliverability.
