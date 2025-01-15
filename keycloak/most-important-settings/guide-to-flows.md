# guide to flows

This is the most important screen for flow managing during the creation of a client:

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-13 085537.png" alt=""><figcaption></figcaption></figure>

|                                          | on                                                                                                                                                                                                                                                               |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Client Authentication**                | The client will or will not be required to insert credentials when accessing Keycloak resources. (1)                                                                                                                                                             |
| **Authorization**                        | You set **detailed rules** for who can access what, considering things like user roles, resource details, even time/location.(2)                                                                                                                                 |
| **implicit flow**                        | [implicit-code-flow.md](../../introduction-to-iam/iam-protocols/oauth-2.0/implicit-code-flow.md "mention")(3)                                                                                                                                                    |
| **OAuth 2.0 Device Authorization Grant** | access on something that hasn' t a webview. authorize access to an application on a device that doesn't have a browser, like a smart TV or IoT device. Instead of logging in directly on the device, the user authenticates on another device with a browser (4) |
| direct access grants                     | allows the client to obtain directly access token/id token without passing by exchanging auth code (5)                                                                                                                                                           |
| **Service Account Roles**                | Service accounts are special identities used by applications, not human users, to access resources. [client-credentials-work-flow.md](../../introduction-to-iam/iam-protocols/oauth-2.0/client-credentials-work-flow.md "mention")(6)                            |
| **OIDC CIBA Grant**                      | _**Usually inutilized and not usefull**_. **Instead of typing**, you use another device you trust, like your laptop or smartwatch, to approve the login using the integration of another idp (7)                                                                 |
| standard flow                            | <p>in oidc response type=code<br>in oauth Authorization code flow (8)</p>                                                                                                                                                                                        |

## More details:

### (1) Client Authentication

**Description**\
Client Authentication is a feature that enforces anyone interacting with the client to provide a username and a service-specific password.

**Default Usage**\
Client Authentication should be enabled by default for all applications requiring authentication. It is strictly necessary when the application consists of two main components: a frontend, such as a user interface, and a backend, which handles the application logic.

**Specific Use Cases**\
For applications that are frontend-only, such as mobile apps or Single Page Applications (SPA) running entirely in the browser, Client Authentication is recommended only if the environment is secure. However, it should not be enabled in insecure environments that cannot be safeguarded, as it would be impossible to protect the secret required for authentication effectively.

**Important Note**\
This setting must be carefully configured to avoid security vulnerabilities tied to the application's operational context. Additional explanations or specific examples can be provided if needed.

### (2) Authorization

The "authorization" switch functions as an API gateway, acting as a security checkpoint for defined endpoints. It ensures that access to these endpoints is allowed only after a valid token has been issued.

**Key Features**

* **Endpoint Protection**: It prevents unauthorized access by intercepting requests and validating them before allowing entry.
* **Token-Based Control**: Access is granted only after the system validates a token, ensuring the integrity and security of the interaction.
* **Advanced Layer of Security**: The authorization switch is a powerful and intricate component, critical for securing APIs and maintaining strict access control.

This layer is essential for environments where robust API security is required, offering both flexibility and a high degree of customization in managing endpoint access.

### (4, 7, 5) Not so useful, disable

### (8, 3) super usefull
