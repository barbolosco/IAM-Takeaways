# SMTP server with GMAIL

**Prerequisites:**

* A Google account with Gmail enabled.
* Access to a computer with an internet connection and a text editor like Notepad or Sublime Text.

**Steps:**

1. **Enable MFA in Gmail:**
   * Sign in to your Gmail account using a web browser.
   * Click on your profile picture in the top-right corner and select "Manage your Google Account."
   * Go to the "Security", enable MFA.
2. **Create an App Password in Google:**
   * Go to the "Security" tab in your Google Account settings (as described in step 1).
   * Scroll down to "Signing in to Google" and click on "App passwords."
   * Select "Select app" and choose "Other (Custom name)."
   * Enter a descriptive name like "Keycloak SMTP" and click "Generate."
   * Google will display a 16-character password. Copy this password securely; you'll need it later.
3. **Configure Keycloak SMTP Settings:**
   * Log in to your Keycloak server's administration console.
   * Navigate to the "Email" tab under "Realm Settings."
   * In the "From" field, enter a sender email address you want to use (e.g., `your_username@gmail.com`).&#x20;
   * The other fields are for aesthetics except for "reply to", in that place you have to insert the same email for consistency.
   * In the "SMTP Server" field, enter `smtp.gmail.com`.
   * Set the "SMTP Port" to `465`.
   * Select the "enable SSL" option for "SSL Security."
   * Enable authentication toggle.
   * In the "Username" field, enter your **full Gmail address** (e.g., `your_username@gmail.com`).
   * In the "Password" field, paste the **16-character app password** you generated in step 2.
4. **Test the SMTP Configuration:**
   * If you haven' done it already go to your Keycloak administration profile and put a valid email address
   * Go to the previous screen (email configuration tab in realm settings) and press "test connection" near to the bottom of the screen.
   * Search for the test mail in your email mailbox and check if the process is concluded successfully

