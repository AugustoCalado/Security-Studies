# OAuth2
OAuth 2 is an authorization framework that enables applications to obtain limited access to user accounts on an HTTP service, such as Facebook and Google. It works by delegating user authentication to the service that **hosts the user account** and authorizing third-party applications to access the user account.

## OAuth Roles

OAuth defines four roles:

-   **Resource Owner**
	- The resource owner is the _user_ who authorizes an _application_ to access their account.
-   **Client**
	- The client is the _application_ that wants to access the _user_’s account. Before that it must be authorized by the user, and the authorization must be validated by the API.
-   **Resource Server**
	- The resource server hosts the protected user accounts,
-   **Authorization Server**
	-	The authorization server verifies the identity of the _user_ then issues access tokens to the _application_.


## Abstract Protocol Flow
![Abstract Protocol Flow](abstractFlowOAhtu2.png)
1. Application (client) request to the user the authorization to access user's service resources.
2. By approving the request of the application (client) the user provides to the application an **authorization grant**
3. The application request an access token from the authorization server. It also send the **authorization grant** acquired from the previous step and its own identity.
4. If both the authorization grand and the application identity were valid thr server issue an access token to the application
5. When the application get an user's resource it must presents the access token for authentication
6. With the right access token presented for the resource server it sends the resource to the application.

## OAuth2 Grant Types
OAuth 2 defines four grant types, each of which is useful in different cases:
-   **Authorization Code**: used with server-side Applications
-   **Implicit**: used with Mobile Apps or Web Applications (applications that run on the user’s device)
-   **Resource Owner Password Credentials**: used with trusted Applications, such as those owned by the service itself
-   **Client Credentials**: used with Applications API access

### Authorization Code
Grant type based on redirection flow, which means that the application must be capable of interacting with the user-agent (i.e. the user’s web browser) and receiving API authorization codes that are routed through the user-agent.
![Abstract Protocol Flow](authCodeFlowOAuth2.png)

1. Give the user **Authorization Code Link**
`https://google.com/v1/oauth/authorize?response_type=code&client_id=CLIENT_ID&redirect_uri=CALLBACK_URL&scope=read`

* https://google.com/v1/oauth/authorize: the API authorization endpoint
* **client_id=client_id**: the application’s _client ID_ (how the API identifies the application)
* **redirect_uri=CALLBACK_URL**: where the service redirects the user-agent after an authorization code is granted
* **response_type=code**: specifies that your application is requesting an authorization code grant
* **scope=read**: specifies the level of access that the application is requesting
> Reference [DigitalOcean](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

2. User Authorizes
When the user cliks the link. The server will prompts the user to authorize the thirdy-party application that is requesting the accesss (User must be logged in to allow this flow)

3. Receiving Authorization Code
With the user's authorization the service redirects the user-agent to the application **redirect URI** (from step 1) along with the **authorization code**

`https://myNiceWebSite.com/callback?code=AUTHORIZATION_CODE`

4. Application Request Access Token
In order to get the access token from the Authorization server the application (client) must inform the **authorization code **.

`https://google.com/v1/oauth/token?client_id=CLIENT_ID&client_secret=CLIENT_SECRET&grant_type=authorization_code&code=AUTHORIZATION_CODE&redirect_uri=CALLBACK_URL`

5. Getting the access token
If the  **authorization code ** is valid, the api will send a response containing the access token. Now the application (client) is authorized and can request user's resource until the token expires or be revoked.

