# 🐬 My sql

Keycloak empowers secure user authentication and authorization for modern applications. To store its data and manage users, it can integrate with various databases. Among these, MySQL shines as a popular and powerful choice for several reasons:

1. **Ubiquity and Familiarity:** MySQL is widely adopted, making it easy to find experienced administrators and resources. Familiarity breeds ease of integration and maintenance.
2. **Robustness and Scalability:** Proven to handle large user bases and heavy loads, MySQL scales efficiently as your needs grow.
3. **Cost-Effectiveness:** Often free and open-source, MySQL helps you manage costs while reaping its functionality.
4. **Rich Ecosystem:** With numerous tools, libraries, and extensions, MySQL integrates seamlessly into various environments.
5. **Community Support:** A vast and active community provides ample help and learning resources.
6. **Flexibility:** MySQL supports various data types and structures, accommodating Keycloak's diverse data needs.
7. **Open Standard Compatibility:** It adheres to industry standards like SQL, ensuring long-term compatibility and data portability.

Installation instructions:

1. press the link to install it on windows: [https://dev.mysql.com/downloads/file/?id=526407](https://dev.mysql.com/downloads/file/?id=526407)
2. open the installer and choose "custom"
3. in the "select products" screen select: server, workbench and shell
4. skip the next screen
5. set your password and username
6. skip the next screen
7. add the \bin to the environment variables

To integrate mysql into keycloak modify the keycloak.conf file like this example (be aware of the username, password and the port):

<details>

<summary>keycloak.conf</summary>

```
# Basic settings for running in production. Change accordingly before deploying the server.

# Database

# The database vendor.

db=mysql

# The username of the database user.

db-username=keycloak

# The password of the database user.

db-password=keycloak

# The full database JDBC URL. If not provided, a default URL is set based on the selected database vendor.

db-url=jdbc:mysql://localhost:3306/keycloak

# Observability

# If the server should expose healthcheck endpoints.

#health-enabled=true

# If the server should expose metrics endpoints.

#metrics-enabled=true

# HTTP

# The file path to a server certificate or certificate chain in PEM format.

#https-certificate-file=${kc.home.dir}conf/server.crt.pem

# The file path to a private key in PEM format.

#https-certificate-key-file=${kc.home.dir}conf/server.key.pem

# The proxy address forwarding mode if the server is behind a reverse proxy.

#proxy=reencrypt

# Do not attach route to cookies and rely on the session affinity capabilities from reverse proxy

#spi-sticky-session-encoder-infinispan-should-attach-route=false

# Hostname for the Keycloak server.

#hostname=myhostname

http-port=8085
```

</details>
