# Install without docker (standalone)

## Windows:

1. Check system requirements (mainly the java version): [https://wjw465150.gitbooks.io/keycloak-documentation/content/server\_installation/topics/installation/system-requirements.html](https://wjw465150.gitbooks.io/keycloak-documentation/content/server\_installation/topics/installation/system-requirements.html)
2. Go on keycloack.org/downloads and install the .zip file (or click here: [https://github.com/keycloak/keycloak/releases/download/23.0.6/keycloak-23.0.6.zip](https://github.com/keycloak/keycloak/releases/download/23.0.6/keycloak-23.0.6.zip))
3. Unzip the folder and put it in a convenient location (ex. "C:/Keycloak-23.0.6")
4. Odd "Keycloak-23.0.6/bin" into environment variables in administrator terminal (ex. `setx /M PATH "%PATH%;C:\Keycloak-23.0.6\bin")`
5. (optional) to get https on kecloak open a terminal in (ex.) "C:/Keycloak-23.0.6" and type the command: (delete line breaks)

{% code overflow="wrap" fullWidth="false" %}
```bash
keytool -genkeypair -storepass password -storetype PKCS12 -keyalg RSA -keysize 2048
-dname "CN=server" -alias server -ext "SAN:c=DNS:localhost,IP:127.0.0.1" -keystore
conf/server.keystore
```
{% endcode %}

1. (optional) go to  "C:keycloak-23.0.6\conf\keycloak.conf" and modify it based on your preferences [keycloak.conf-guide.md](keycloak.conf-guide.md "mention")
2. Close and re-open the terminal, and type the command kc.bath start-dev
