# keycloak.conf guide

## Setting up the database connection

To configure the database connection for Keycloak, follow these steps:

* **Step 1:** Locate the `Database` section in the configuration file.
* **Step 2:** Uncomment and modify the following parameters based on your database setup:
  * `db`: Set the database vendor (e.g., `postgres`, `mysql`, `mssql`, etc.).
  * `db-username`: Provide the username of the database user.
  * `db-password`: Set the password of the database user.
  * `db-url`: Specify the full database JDBC URL.

Example:

```conf
# Database
db=postgres
db-username=myuser
db-password=mypassword
db-url=jdbc:postgresql://localhost/mydatabase
```

#### Note: You might want to configure a native database for example Mysql instead of the native Postgress.

```
#database vendor
db=mysql
# The username of the database user.
db-username=keycloak
# The password of the database user.
db-password=keycloak
# The full database JDBC URL. If not provided, a default URL is set based on the selected database vendor.
db-url=jdbc:mysql://localhost:3306/keycloak
```

## Enabling Observability

To enable healthcheck and metrics endpoints for observability, follow these steps:

* **Step 1:** Locate the `Observability` section in the configuration file.
* **Step 2:** Set the desired options by modifying the following parameters:
  * `health-enabled`: Set to `true` to enable healthcheck endpoints.
  * `metrics-enabled`: Set to `true` to enable metrics endpoints.

Example:

```conf
# Observability
health-enabled=true
metrics-enabled=true
```

## Configuring HTTPS settings

To configure HTTPS settings and hostname for the Keycloak server, follow these steps:

* **Step 1:** Locate the `HTTP` section in the configuration file.
* **Step 2:** Modify the following parameters as per your requirements:
  * `https-certificate-file`: Set the file path to the server certificate or certificate chain in PEM format.
  * `https-certificate-key-file`: Set the file path to the private key in PEM format.
  * `hostname`: Specify the hostname for the Keycloak server (default->localhost).
  * `http-port`: Specify the port for the Keycloak server (default->8080 however 8080 is a commonly used port so it is always recommended to check in the command shell with administrator privileges the used ports windows -> `netstat -ab`  linux -> `sudo netstat -tulpn`  ).

Example:

```conf
# HTTP
https-certificate-file=/path/to/server.crt.pem
https-certificate-key-file=/path/to/server.key.pem
hostname=myhostname
http-port=8085
```
