# Cross-Origin Resource Sharing

Cross-Origin Resource Sharing (CORS) is a mechanism that enables web browsers to make controlled requests to resources located on a different domain, protocol, or port than the one that serves the web page. This allows websites to use resources from various origins for enhanced functionality and user experience, while maintaining security through controlled access.

#### Same-Origin Policy (SOP)

To fully comprehend CORS, it is crucial to first understand the Same-Origin Policy (SOP). The SOP is a security measure enforced by web browsers that limits websites from accessing resources on different origins. This restriction is in place to prevent malicious scripts from stealing sensitive data or hijacking user sessions.

#### How CORS works?

1. **Request with Origin Header:** When a web page initiates a request to a resource of a different origin, the browser automatically adds an `Origin` header to the request. This header contains information about the origin of the page making the request.
2. **Server Response with CORS Headers:** The server receiving the request checks if it has CORS headers configured. These headers specify which origins are allowed to access its resources:
   * **`Access-Control-Allow-Origin`:** This header defines origins that are allowed to make requests to the server. It can be set to `*` to allow any origin, but for security reasons, it's usually restricted to specific origins.
   * Other CORS headers can be used to control:
     * **Allowed HTTP methods:** Which methods (e.g., `GET`, `POST`, `PUT`, `DELETE`) are allowed for requests from specific origins.
     * **Allowed request headers:** Which additional headers the client can send in the request.
     * **Credentials:** Whether credentials (such as cookies) are allowed in the request.
3. **Access Granted or Denied:** Based on the CORS headers present and their configuration, the server:
   * **Grants access:** If the origin matches the allowed origins and other conditions are met, the server sends the requested resource along with appropriate CORS headers.
   * **Denies access:** If the origin doesn't match or other conditions aren't met, the server sends an error response, and the browser blocks access to the resource.

#### Pre-flight Requests (OPTIONS)

For certain requests involving additional headers or sending credentials (e.g., `POST`, `PUT`, `DELETE`), the browser might send a pre-flight request (using the `OPTIONS` method) to the server before making the actual request. This pre-flight request allows the server to indicate if the actual request would be allowed, based on its CORS configuration.

**Cross-Origin Requests and Security Implications**

To understand CORS, it is important to first understand the Same-Origin Policy (SOP). The SOP is a security measure enforced by web browsers that limits websites from accessing resources on different origins. This restriction is in place to prevent malicious scripts from stealing sensitive data or hijacking user sessions.

**Risks of Misconfigured CORS Policies**

* **Data Exposure**: Without CORS properly configured, sensitive data could be exposed to unauthorized origins, leading to data breaches and privacy violations.
* **Cross-Site Request Forgery (CSRF)**: Inadequate CORS configuration may enable malicious websites to forge requests from a user's browser to a trusted origin, potentially leading to unauthorized actions or data manipulation.
* **Information Leakage**: Misconfigured CORS policies might inadvertently leak information about the server's internal structure or sensitive data, providing attackers with valuable insights for further exploitation.
* **Session Hijacking**: Lack of CORS controls could facilitate session hijacking attacks, where attackers exploit cross-origin requests to steal session tokens and impersonate legitimate users.

**Common CORS Misconfigurations**

* **Wildcard Allowances**: Allowing access from any origin (`*`) without proper validation can open the door to exploitation, as it effectively nullifies CORS protections.
* **Insufficient Validation**: Failing to validate the `Origin` header or blindly trusting user-supplied values can result in unauthorized access to sensitive resources.
* **Insecure Headers**: Improper configuration of CORS headers, such as missing or misconfigured `Access-Control-Allow-Origin` headers, can lead to inconsistent enforcement of CORS policies.
* **Excessive Permissions**: Granting overly broad permissions (e.g., allowing all HTTP methods or headers) increases the attack surface and undermines the principle of least privilege.
