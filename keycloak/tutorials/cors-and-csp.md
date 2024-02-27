# CORS and CSP

### CORS

It is likely that you stumbled upon [CORS](../../iam-introduction/iam-protocols/cross-origin-resource-sharing.md) due to an error:

```markup
Access to fetch at 'https://example.com' from origin 'http://example.com'
has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header 
is present on the requested resource. If an opaque response serves your needs,
set the request's mode to 'no-cors' to fetch the resource with CORS disabled.
```

This occurs because there's a discrepancy between the headers of the request you're attempting to send to a specific website and the security protocols governing access to that website.

To elaborate, when a website's server receives a request, it needs to verify and control the source of that request. Therefore, if an attacker replicates a legitimate request, such as accessing the website's data, but sends it from an unknown origin, CORS (Cross-Origin Resource Sharing) blocks it as an additional security measure to safeguard the integrity of the website.

This control can be managed on the server-side, where the website is hosted (apache, lighthttpd,  ...) and/or on the frameworks and platforms built-in mechanisms or middleware (keycloak, okta, ....). Here are some examples on how to do it:

### In Apache (windows)

1. **Access Apache Configuration:**
   * Navigate to the directory where Apache is installed on your Windows system. This is typically `C:\Program Files\Apache Software Foundation\Apache[version]\`.
2. **Locate the configuration files:**
   * Open the `conf` folder within the Apache directory.
   * Look for the `httpd.conf` file, which is the main configuration file for Apache.
3. **Edit httpd.conf:**
   * Right-click on `httpd.conf` and open it in a text editor (e.g., Notepad++).
4. **Enable mod\_headers:**
   *   Before configuring CORS, ensure that the `mod_headers` module is enabled. Look for the following line in `httpd.conf`:

       ```markup
       #LoadModule headers_module modules/mod_headers.so
       ```
   * Remove the `#` at the beginning of the line to uncomment it, enabling the module.
5. **Configure CORS:**
   *   Add the following lines to `httpd.conf` to set up CORS policies:

       ```xml
       <IfModule mod_headers.c>
           Header set Access-Control-Allow-Origin "*"
           Header set Access-Control-Allow-Methods "GET, POST, OPTIONS"
           Header set Access-Control-Allow-Headers "Content-Type, Authorization"
       </IfModule>
       ```
6. **Save the changes:**
   * After making the necessary changes, save the `httpd.conf` file.
7. **Restart Apache:**
   * To apply the new CORS configuration, restart the Apache server.
     * Open Command Prompt as an administrator.
     *   Execute the following command to restart Apache:

         ```
         httpd -k restart
         ```

### In keycloak

1. go to administration console (usually http://localhost:8080/)
2. choose your realm in the top left settings
3. go to clients in the left menu and select the desired one
4. scroll down untill you see the "Access settings"
5. set "Valid redirect URIs"(mandatory), "Valid post logout redirect URIs", "Web origins"(mandatory), "Admin URL" in the right way.
6. remember to save and reload the tabs

<details>

<summary>what are those keycloak settings?</summary>

Valid redirect URIs->Valid URI pattern a browser can redirect to after a successful login. Simple wildcards are allowed such as 'http://example.com/_'. Relative path can be specified too such as /my/relative/path/_. Relative paths are relative to the client root URL, or if none is specified the auth server root URL is used. For SAML, you must set valid URI patterns if you are relying on the consumer service URL embedded with the login request.\
\
Valid post logout redirect URIs->Valid URI pattern a browser can redirect to after a successful logout. A value of '+' or an empty field will use the list of valid redirect uris. A value of '-' will not allow any post logout redirect uris. Simple wildcards are allowed such as 'http://example.com/_'. Relative path can be specified too such as /my/relative/path/_. Relative paths are relative to the client root URL, or if none is specified the auth server root URL is used.

Web origins->Allowed CORS origins. To permit all origins of Valid Redirect URIs, add '+'. This does not include the '_' wildcard though. To permit all origins, explicitly add '_'.

Admin URL->URL to the admin interface of the client. Set this if the client supports the adapter REST API. This REST API allows the auth server to push revocation policies and other administrative tasks. Usually this is set to the base URL of the client.

</details>

### CSP

**Why implement CSP?**

Content Security Policy (CSP) is a powerful security mechanism that mitigates risks associated with Cross-Site Scripting (XSS) attacks, data injection vulnerabilities, and unauthorized resource loading. By defining trusted sources for scripts, styles, images, and other resources, you can significantly improve the security posture of your website.

**Where to Set CSP:**

CSP can be enforced in various ways, but one effective approach is configuring your web server to send the appropriate CSP header with every HTTP response. This ensures consistent policy application across your entire website.

**How to Set CSP in Apache (Windows):**

**3.1. Accessing Apache Configuration:**

* Navigate to the directory where Apache is installed on your Windows system. The typical location is `C:\Program Files\Apache Software Foundation\Apache\[version]\`.

**3.2. Locate Configuration Files:**

* Open the `conf` folder within the Apache directory.

**3.3. Edit `httpd.conf`:**

* Right-click on `httpd.conf` and choose a text editor (e.g., Notepad++) to open it.

**3.4. Enable `mod_headers`:**

* Ensure the `mod_headers` module is enabled. Look for the following line:

```
#LoadModule headers_module modules/mod_headers.so
```

* Uncomment the line by removing the `#` symbol at the beginning.

**3.5. Configure CSP:**

* Add the following lines to `httpd.conf` to establish your CSP:

Apache

```xml
<IfModule mod_headers.c>
    Header always set Content-Security-Policy "script-src 'self'; style-src 'self'; img-src 'self';"
</IfModule>
```

**Explanation of the CSP Directive:**

* This example defines a basic CSP that allows resources (scripts, styles, and images) only from the same origin (`'self'`). You can customize this directive based on your specific needs. Refer to [https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP) for detailed information on available directives and allowed values.

**3.6. Save Changes:**

* Save the `httpd.conf` file after making the necessary edits.

**3.7. Restart Apache:**

* To apply the new CSP configuration, restart the Apache server. Open a command prompt as administrator and execute:

```
httpd -k restart
```
