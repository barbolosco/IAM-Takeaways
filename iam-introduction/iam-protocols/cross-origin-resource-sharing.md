# Cross-Origin Resource Sharing

Cross-Origin Resource Sharing (CORS) is a mechanism that allows web browsers to make controlled requests to resources located on a different domain, protocol, or port than the one that served the web page. This flexibility enables websites to leverage resources from various origins for enhanced functionality and user experience, while maintaining security through controlled access.

#### Same-Origin Policy (SOP)

Before diving into CORS, it's essential to understand the Same-Origin Policy (SOP). SOP is a security feature implemented by web browsers to restrict websites from directly accessing resources located on different origins. This restriction prevents malicious scripts from stealing sensitive data or hijacking user sessions.

#### How CORS Works

1. **Request with Origin Header:** When a web page initiates a request to a resource on a different origin, the browser automatically adds an `Origin` header to the request. This header contains information about the origin of the page making the request.
2. **Server Response with CORS Headers:** The server receiving the request checks if it has CORS headers configured. These headers specify which origins are allowed to access its resources:
   * **`Access-Control-Allow-Origin`:** This header defines origins that are allowed to make requests to the server. It can be set to `*` to allow any origin, but for security reasons, it's usually restricted to specific origins.
   * Other CORS headers can be used to control:
     * **Allowed HTTP methods:** Which methods (e.g., `GET`, `POST`, `PUT`, `DELETE`) are allowed for requests from specific origins.
     * **Allowed request headers:** Which additional headers the client can send in the request.
     * **Credentials:** Whether credentials (such as cookies) are allowed in the request.
3. **Access Granted or Denied:** Based on the CORS headers present and their configuration, the server:
   * **Grants access:** If the origin matches the allowed origins and other conditions are met, the server sends the requested resource along with appropriate CORS headers.
   * **Denies access:** If the origin doesn't match or other conditions aren't met, the server sends an error response, and the browser blocks access to the resource.

#### Preflight Requests (OPTIONS)

For certain requests involving additional headers or sending credentials (e.g., `POST`, `PUT`, `DELETE`), the browser might send a preflight request (using the `OPTIONS` method) to the server before making the actual request. This preflight request allows the server to indicate if the actual request would be allowed, based on its CORS configuration.
