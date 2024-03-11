# PKCE

Proof Key for Code Exchange (PKCE) is an extension to the OAuth 2.0 Authorization Code Flow that enhances the security of authorization code exchanges. It does so by introducing a verifier and a code challenge, which together prevent unauthorized applications from obtaining access tokens, even if they steal the authorization code.

Understanding the problem

In the traditional Authorization Code Flow, the authorization server generates an authorization code and sends it to the client application after successful user authentication. The client then exchanges this code for an access token, which grants access to user resources on the resource server. However, if a malicious application intercepts this authorization code, it can impersonate a legitimate application and gain unauthorized access to user resources.

How PKCE Works

1.**Client Generated Verifier and Code Challenge:**

* The client application generates a random secret value called the **verifier**.
* It then creates a **code challenge** by applying a specific cryptographic function (e.g., base64 URL encoding and SHA-256 hashing) to the verifier.

2.**Client Sends Code Challenge:**

* The client application includes the code challenge in the initial authorization request sent to the authorization server. This code challenge is typically sent as a parameter called code\_challenge.

3.**Authorization Code Exchange:**

* After successful user authentication, the authorization server generates an authorization code and sends it back to the client application.

4.**Client Generated Code Verifier:**

* Upon receiving the authorization code, the client application generates the same **verifier** used in step 1.

5.**Client Sends a Token Request:**

* The client application sends a token request to the token endpoint of the authorization server, including:
  * The authorization code.
  * The previously generated verifier (hashed with the same function used for the code challenge).

6.**Authorization Server Verified Code:**

* The authorization server verifies the code.
* It then calculates the code challenge based on the received verifier using the same cryptographic function.
* Finally, it compares the calculated code challenge with the one received during the initial authorization request.

7.**Access Token Granted (if valid):**

* If the code challenge matches, the authorization server can confirm that the request came from the legitimate client application that initially created the code challenge. The server will then provide the client with an access token, which will allow it to access user resources on the resource server.

Benefits of PKCE

* **Enhanced Security:**PKCE reduces the risk of authorization code theft. Even if an attacker intercepts the code, they cannot generate the matching verifier required to obtain an access token.
* **Improved Application Security:** PKCE is especially useful for public client applications, such as mobile apps and browser extensions, which are more vulnerable to code theft due to their exposed nature.
