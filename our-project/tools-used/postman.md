# 📬 Postman

**Step 1: Obtain Access Token using OpenID Connect Authorization Flow**

1. **Launch Postman:** Open Postman and create a new **GET** request targeting your API endpoint (e.g., [https://mockbin.org/request](https://mockbin.org/request)).
2. **Initiate Authorization Flow:** Go to **Authorization** -> **OAuth 2.0** and choose **Authorization Code** as the grant type.
3. **Configure OAuth2 Settings:**
   * **Auth URL:** In Keycloak, navigate to **Realm Settings** -> **OpenID Connect Endpoint Configurations**. Copy the **Authorization Endpoint** URL.
   * **Access Token URL:** Paste the **Token Endpoint** URL from Keycloak's OpenID Connect Endpoint Configurations.
   * **Client ID & Secret:** In Keycloak, create a new **OpenID Connect** client named "Postman." Enable **Client Authentication** and retrieve the generated **Client ID** and **Client Secret**. Keep the Client Secret secure.
   * **Scope:** Add `openid` to the scope field to enable OpenID Connect. Leave **State** empty.
4. **Get New Access Token:** Click **Get New Access Token**. A Keycloak login window will appear.
5. **Log in to Keycloak:** Provide your Keycloak realm user credentials to authorize access.
6. **Receive Access Token:** Upon successful login, Postman will store the returned access token.

**Step 2: Call API using Postman**

1. **Set Authorization Header:** In your Postman request, navigate to **Authorization** -> **Bearer Token**. Enter the received access token in the **Token** field.
2. **Send Request:** Click **Send** to execute your API request. The access token will be automatically included for authorization.\




<details>

<summary>Some screenshots</summary>



</details>
