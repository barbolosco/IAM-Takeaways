# SMTP server with GMAIL

**Prerequisites:**

* A Google account with Gmail enabled.
* Access to a computer with an internet connection and a text editor like Notepad or Sublime Text.

**Steps:**

1. **Enable Less Secure App Access in Gmail:**
   * Sign in to your Gmail account using a web browser.
   * Click on your profile picture in the top-right corner and select "Manage your Google Account."
   * Go to the "Security" tab and scroll down to "Less secure app access."
   * **Caution:** Enabling this setting reduces security and might make your account more vulnerable to attacks. It's recommended to disable it after completing the setup and only enable it when necessary.
   * Click on "Turn on less secure app access."
2. **Create an App Password in Google:**
   * Go to the "Security" tab in your Google Account settings (as described in step 1).
   * Scroll down to "Signing in to Google" and click on "App passwords."
   * Select "Select app" and choose "Other (Custom name)."
   * Enter a descriptive name like "Keycloak SMTP" and click "Generate."
   * Google will display a 16-character password. Copy this password securely; you'll need it later.
3. **Configure Keycloak SMTP Settings:**
   * Log in to your Keycloak server's administration console.
   * Navigate to the "Mail" tab under "Server Settings."
   * In the "SMTP Server" field, enter `smtp.gmail.com`.
   * Set the "SMTP Port" to `587`.
   * Select the "STARTTLS" option for "TLS Security."
   * In the "From" field, enter a sender email address you want to use (e.g., `keycloak@yourdomain.com`). **Note:** Replace `yourdomain.com` with a placeholder if you don't have a domain. However, using an email address with your domain name is highly recommended for better email deliverability and security.
   * In the "Username" field, enter your **full Gmail address** (e.g., `your_username@gmail.com`).
   * In the "Password" field, paste the **16-character app password** you generated in step 2.
4. **Test the SMTP Configuration:**
   * In the Keycloak administration console, go to the "Users" tab and select a user.
   * Click on the "Credentials" tab and then "Reset Password."
   * Enter a new password for the user and click "Reset Password."
   * Check your email inbox (including spam folders) for a password reset email from Keycloak. If you receive the email, the SMTP configuration is successful.

**Additional Considerations:**

* **Domain-Based Message Authentication (DKIM) and Sender Policy Framework (SPF):** While not strictly required, implementing DKIM and SPF with a custom domain can significantly improve email deliverability and prevent spoofing.
* **Improved Security:** If possible, consider using a dedicated email service provider (ESP) that offers more robust security features specifically designed for sending transactional emails.
