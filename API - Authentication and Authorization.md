# API - Authentication and Authorization



### HTTP Authentication
![HTTP Authentication Schemes](HTTP Authentication Schemes.png)

### Authentication vs Authorization
* **Authentication** is when an entity proves an identity. In other words, **Authentication** proves that you are who you say you are.

* **Authorization** Authorization is when an entity proves a right to access. In other words, Authorization proves you have the right to make a request. 

### HTTP Basic Authentication
An HTTP user agent simply provides a username and password to prove their authentication. This approach uses the **HTTP header** in the form of `Authorization: Basic <credentials>`, where credentials is the base64 encoding of id and password joined by a single colon `:`. 

**Warning**: Although it encrypts the credentials to the base64 encode, the credentials are **NOT encrypted**.

### HTTP Bearer Authentication
Bearer authentication (also called token authentication) is a HTTP authentication that uses security tokens called bearer tokens.

The token of this authentication is a cryptic string (e.g. JWT)
`Authorization: Bearer <token>`

#### JWT
> JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. [font](https://jwt.io/introduction/)

**Integrity**
One good point of using JWT is the integrity of the informatioin contained within the JSON Web Token. Thus there are the guarantee that the contend was not motified. Alson when tokens are signed, the signature alsos certifies that only the party holding the private key is the on that signed it.

**When use JWT**
* **Authorization:** Once user is logged in, each subsequent request will inclide the JWT, allowing the user to access routes, services etc;
* **Information Exchange:** JWT securely transmitting information between parties. Since it is signed, there is the assurance that the senders are who they say they are. Moreover, as the signature is calculated using the header and the payload, it is possible to verify that the content has not been tampered with.

**JWT Structure**
JSON Web Tokens consist of three parts separated by dots (.) `xxxxx.yyyyy.zzzzz` 

Which are:
* Header: consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.
* Payload:  contains the claims (statements about an entity). There are alsol registred claim used by the JWT [see](https://tools.ietf.org/html/rfc7519#section-4.1)
* Signature


### API Keys
An application programming interface key (API key) is a **unique identifier** (secret token) which is submitted alongside web service (or similar) requests in order to identify the origin of the request. 

**Warning:** is that API keys are often used for what they’re not – an API key is not a method of authorization, it’s a method of authentication. 

#### Why and when to use API keys
**API keys are for projects, authentication is for users**, in other words, API keys identify the calling project (application or site) making the call to an API. on the other hand, authentication tokens identify a user (person), that is using the app or site.

![Abstract Protocol Flow](Resources/api_keys_overview.png)

By identifying the calling project, you can use API keys to associate usage information with that project.

API keys are generally not considered secure; they are typically accessible to clients, making it easy for someone to steal an API key. Once the key is stolen, it has no expiration, so it may be used indefinitely, unless the project owner revokes or regenerates the key.

#### When to use API Keys?
* Block anonymous traffic. API keys identify an application's traffic. That maybe is useful if there are some need to debug an issue or show the application's usage
* Controll the number of call made to your API
* Identify usage pattern
* Filter logs by API Keys

#### When not use API Keys?
* Identify individual users
* Secure authorization
* identify the creators of a project

#### Handling API Keys
* Do not embed API keys directly in code. Instead of embedding your API keys in your applications, store them in environment variables or in files outside of your application's source tree.

### OAuth
OAuth is an open-standard authorization protocol or framework that describes how unrelated servers and services can safely allow authenticated access to their assets without actually sharing the initial, related, single logon credential.

### OAuth 2
OAuth 2 is an authorization framework that enables applications to obtain limited access to user accounts on an HTTP service, such as Facebook and Google. It works by delegating user authentication to the service that **hosts the user account** and authorizing third-party applications to access the user account.

### OpenID
OpenID is an open standard for authentication. 

### OpenID Connect 
OpenID Connect is an identity layer on top of the OAuth 2.0 protocol. It allows clients o request and receive information about authenticated sessions as well as providing access to backend APIs using OAuth 2.0 tokens. In short, It gives an identity provider the ability to provide clients with enduser's identication and basic profile information.

 It uses JWTs (JSON Web Tokens) as identity token format.

The **Key Distribution** provided by OpenID Connect is called JSON Web Key Set (JWKS).

**User Information**
OpenID Connect provides endpoints for Clients to use when they need access to user data. It also provides mechanisms for the user to consent before this data is released to the client.

**OpenID Connect Core Features**
-   Core: authentication and use of Claims to communicate End-User information
-   Discovery: stipulates how a client can dynamically determine information about OpenID Providers
-   Dynamic Registration: dictates how a client can register with a provider
-   Session Management: defines how to manage OIDC sessions

### OpenID vs OAuth
"OpenID is for humans logging into machines, OAuth is for machines logging into machines on behalf of humans."

### SAML
It’s an open standard that provides both authentication and authorization.

## Authorization
### Role-Based Access Control
### Attribute-Based Access Control
### Delegated Access Control with OAuth 2.0



## References
[3-common-methods-api-authentication-explained/](https://nordicapis.com/3-common-methods-api-authentication-explained/)
[when-why-api-key#security_of_api_keys](https://cloud.google.com/endpoints/docs/openapi/when-why-api-key#security_of_api_keys)
[authentication - api-keys](https://cloud.google.com/docs/authentication/api-keys)
[An Introduction to OAuth 2](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)
[openid vs oauth vs saml/](https://spin.atomicobject.com/2016/05/30/openid-oauth-saml/)
[what-is-oauth-how-the-open-authorization-framework-works](https://www.csoonline.com/article/3216404/what-is-oauth-how-the-open-authorization-framework-works.html)





