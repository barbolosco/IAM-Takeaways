# IAM solutions

Before the emergence of OpenID Connect and modern IAM services, websites such as Yelp attempted to connect user accounts with third-party services. However, early implementations, like Yelp's, were often unsafe and lacked robust authentication and authorization mechanisms that are now standard.&#x20;

Yelp asked users for their Google passwords to create an Identity Provider (IDP), which posed a significant security risk. It is uncommon for a reputable service to ask for your password for another service. These outdated systems often use insecure methods for password sharing or data transfer, which can leave user data vulnerable to unauthorized access and breaches.&#x20;

The introduction of OpenID Connect and modern IAM services has revolutionized the way websites and applications manage user identities and access to third-party resources. These services offer a secure and standardized method for users to authenticate themselves and grant access to their data, without sharing sensitive information such as passwords.&#x20;

The market offers a variety of IAM solutions, each with its own strengths and weaknesses. Some of the most popular IAM solutions are:



<table><thead><tr><th width="85"></th><th width="171">Okta</th><th>Monokee</th><th>keycloak</th></tr></thead><tbody><tr><td>+</td><td>Ease of use, Pre-built integrations, Scalable,<br>Secure</td><td>Customizable, flexible, security focus</td><td><p>Open source, flexible, scalable, </p><p>community support </p></td></tr><tr><td>-</td><td>Cost, Vendor lock-in, Limited self-hosting</td><td>more complex, limited support, less mature</td><td>more complex, limited features, customization burden</td></tr></tbody></table>
