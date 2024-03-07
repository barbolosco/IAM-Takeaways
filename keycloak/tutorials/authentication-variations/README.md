# Authentication variations

Welcome to the documentation page on authentication variations in Keycloak. In this chapter, we will explore the diverse tools available within Keycloak that can enhance the security and user experience of the login process. Before delving into the details, let's provide a brief overview of what this chapter entails.

### Overview

Authentication is a critical aspect of any application's security infrastructure. Keycloak, a robust identity and access management solution, offers a plethora of tools and methods to fortify the authentication process. In this chapter, we will explore various authentication methods and technologies supported by Keycloak, each tailored to meet different security requirements and user preferences.

#### Authentication Methods:

* **SMS:** Utilize SMS (Short Message Service) for authentication purposes, sending one-time passcodes to users' mobile devices.
* **Email:** Authenticate users through email, providing a secure verification process via email tokens.
* **Auth Apps:** Employ authentication apps such as Google Authenticator or Authy for generating time-based one-time passcodes (TOTP) or HMAC-based one-time passwords (HOTP).
* **WebAuthn:** Implement WebAuthn, enabling passwordless authentication or utilizing external authenticators like security keys.
* **Passkeys:** Employ passkeys, which are cryptographic keys used for authentication and encryption.
* **Social Login (as IdP):** Allow users to authenticate using their social media accounts as identity providers (IdPs), leveraging platforms like Google, Facebook, or Twitter.
* **Browser Storages (Cookies and Sessions):** Utilize browser storage mechanisms such as cookies and sessions for maintaining user authentication state.

#### Methods for Authentication:

* **OTP (One-Time Passcode):** Generate and send one-time passcodes to users via SMS or email for authentication purposes.
* **TOTP (Time-Based One-Time Password):** Utilize time-based algorithms to generate one-time passcodes that are valid for a short period, often implemented through authentication apps.
* **Verification:** Verify users' phone numbers or email addresses to ensure the authenticity of their identities.
* **Complete Verification:** Delegate the authentication process entirely to a designated tool like Google Authenticator, which handles the entire authentication task.
