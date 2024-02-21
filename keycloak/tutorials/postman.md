# 📬 Postman

Postman is an application to test (Keycloak in this case) APIs. To clarify, is an app that can be used to send and recive API calls before inserting them into proper code of your software.\


The app is very straightforward to use. Here is a simple guide to follow after it's installation from [https://www.postman.com/downloads/](https://www.postman.com/downloads/)\


**Launching Postman:**

1. Once installed, open the Postman application.
2. The main interface will display a workspace for building and managing your API requests.

**Setting Up a Keycloak API Request:**

1. **Create a Collection:**
   * In the left sidebar, click on "Collections" and then "Create Collection."
   * Give your collection a name (e.g., "My Keycloak Tests").
2. **Create a Request:**
   * Within your collection, click on "New Request."
   * Set the request method (e.g., GET, POST, PUT, etc.) based on the Keycloak API endpoint you want to test.
   * Enter the API endpoint URL in the address bar.
3. **Add Headers (if required):**
   * Some Keycloak API calls require specific headers for authentication or authorization.
   * Click on the "Headers" tab and add the necessary headers and their values.
4. **Add Body (if required):**
   * For POST or PUT requests, you may need to send data in the request body.
   * Choose the appropriate format (e.g., JSON, form-data) and enter the data in the "Body" tab.
5. **Send the Request:**
   * Click the "Send" button to execute the request to the Keycloak API endpoint.
6. **View the Response:**
   * The response from the API will be displayed in the "Response" tab.
   * This includes the status code, headers, and response body (if any).

### Advices for keycloak users:

* The api links is likely to coincide with keycloak endpoints:\
  http://{host}:{port}/realms/{realm}/protocol/{protocol}/{token or auth}\
  example:\
  http://localhost:8085/realms/myrealm/protocol/openid-connect/token
* in the "body" tab keycloak uses "x-www-form-urlencoded"&#x20;
* in the authorization endpoint a "GET" type request is needed, while in the token endpoint is needed a "POST"\
