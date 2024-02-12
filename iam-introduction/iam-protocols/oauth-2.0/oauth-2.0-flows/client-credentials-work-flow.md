# Client credentials work flow

The Client Credentials flow is used when the client is acting on its own behalf rather than on behalf of a specific user. In this flow, the client sends its own credentials (client ID and client secret) directly to the authorization server. Upon successful validation of the client credentials, the authorization server issues an access token to the client. This access token can then be used by the client to access protected resources that are not associated with any particular user. This flow is commonly used for machine-to-machine communication or for accessing backend services where user authentication is not required.

<figure><img src="https://learn.microsoft.com/en-us/entra/identity-platform/media/v2-oauth2-client-creds-grant-flow/convergence-scenarios-client-creds.svg" alt="" width="563"><figcaption></figcaption></figure>
