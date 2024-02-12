# authorization code flow

By default there is a single realm, master, and by login to the admin console user will login to master realm. The master realm is  for administration purposes and you need to create a new realm, myRealm.

<figure><img src="https://embriq.no/wp-content/uploads/2022/10/Add-relam.png" alt=""><figcaption></figcaption></figure>

After switching to the newly created realm, myRealm, create a new client.

<figure><img src="https://embriq.no/wp-content/uploads/2022/10/myRelam.png" alt=""><figcaption></figcaption></figure>

* Disable “Direct Access Grants Enabled”
* “Access Type” to “confidential”
* “Valid Redirect” to redirect back to after successful login

<figure><img src="https://embriq.no/wp-content/uploads/2022/10/Skjermbilde.png" alt=""><figcaption></figcaption></figure>

After saving, client\_id and client\_secret can be retrieved from “Credentials” tab\


<figure><img src="https://embriq.no/wp-content/uploads/2022/10/MyClient.png" alt=""><figcaption></figcaption></figure>

## URL to access authentication page on keycloak:

http://localhost:8080/realms/myRealm/protocol/openid\
\-connect/auth?response\_type=code\&client\_id=myClient\&redirect\_uri=\
http%3A%2F%2Flocalhost%3A12345%2Fcallback\&scope=openid\&state=something

This URL for keycloak will redirect you to the login page for keycloak. After successful login keycloak will redirect you back to the defined redirect\_uri .

Now the client application by receiving the authorization code from the above call can make a request to keycloak with code + client ID + client secret  to get access token and ID token.

Here is the curl command for getting access token and ID token:

curl -X POST http://localhost:8080/realms/myRealm/protocol/openid-connect/token \\\
–data grant\_type=authorization\_code \\\
–data ‘client\_id=myClient’ \\\
–data client\_secret=\<PUT CLIENT SECRET HERE> \\\
–data code=\<PUT CODE HERE> \\\
–data ‘redirect\_uri=http%3A%2F%2Flocalhost%3A12345%2Fcallback’
