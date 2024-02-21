# flow management

This is the most important screen for flow managing during the creation of a client:

<figure><img src="../../../.gitbook/assets/Screenshot 2024-02-13 085537.png" alt=""><figcaption></figcaption></figure>



|                                           | on                                                                                                                                                                                                                                                 |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Client Authentication**                 | The client will not be required to provide credentials when accessing Keycloak resources                                                                                                                                                           |
| **Authorization**                         | You set **detailed rules** for who can access what, considering things like user roles, resource details, even time/location.                                                                                                                      |
| **implicit flow**                         | [implicit-code-flow.md](../../../iam-introduction/iam-protocols/oauth-2.0/oauth-2.0-flows/implicit-code-flow.md "mention")                                                                                                                         |
| **OAuth 2.0 Device Authorization Grant**  | authorize access to an application on a device that doesn't have a browser, like a smart TV or IoT device. Instead of logging in directly on the device, the user authenticates on another device with a browser                                   |
| direct access grants                      | allows the client to obtain directly access token/id token without passing by exchanging auth code                                                                                                                                                 |
| **Service Account Roles**                 | Service accounts are special identities used by applications, not human users, to access resources. [client-credentials-work-flow.md](../../../iam-introduction/iam-protocols/oauth-2.0/oauth-2.0-flows/client-credentials-work-flow.md "mention") |
| **OIDC CIBA Grant**                       | **Instead of typing**, you use another device you trust, like your laptop or smartwatch, to approve the login using the integration of another idp                                                                                                 |
| standard flow                             | <p>in oidc response type=code<br>in oauth Authorization code flow</p>                                                                                                                                                                              |
