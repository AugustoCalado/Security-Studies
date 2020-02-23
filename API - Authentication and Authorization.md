# API - Authentication and Authorization



## HTTP Authentication
![HTTP Authentication Schemes](HTTP Authentication Schemes.png)

### Authentication vs Authorization
**Authentication** is when an entity proves an identity. In other words, **Authentication** proves that you are who you say you are.
**Authorization** Authorization is when an entity proves a right to access. In other words, Authorization proves you have the right to make a request. 

### HTTP Basic Authentication
An HTTP user agent simply provides a username and password to prove their authentication. This approach uses the **HTTP header** in the form of `Authorization: Basic <credentials>`, where credentials is the base64 encoding of id and password joined by a single colon `:`. 

**Warning**: Although it encrypts the credentials to the base64 encode, the credentials are **NOT encrypted**.

### HTTP Bearer Authentication
Bearer authentication (also called token authentication) is a HTTP authentication that uses security tokens ccalled bearer tokens.

The token of this authentication is a cryptic string (e.g. JWT)
`Authorization: Bearer <token>`

#### JWT

### API Keys
An application programming interface key (API key) is a **unique identifier** (secret token) which is submitted alongside web service (or similar) requests in order to identify the origin of the request. 

**Warning:** is that API keys are often used for what they’re not – an API key is not a method of authorization, it’s a method of authentication. 

#### Why and when to use API keys
**API keys are for projects, authentication is for users**, in other words, API keys identify the calling project (application or site) making the call to an API. on the other hand, authentication tokens identify a user (person), that is using the app or site.

![Abstract Protocol Flow](Resources/api_keys_overview.png)

By identifying the calling project, you can use API keys to associate usage information with that project.

API keys are generally not considered secure; they are typically accessible to clients, making it easy for someone to steal an API key. Once the key is stolen, it has no expiration, so it may be used indefinitely, unless the project owner revokes or regenerates the key.

### When to use API Keys
* Block anonymous traffic. API keys identify an application's traffic. That maybe is useful if there are some need to debug an issue or show the application's usage
* Controll the number of call made to your API
* Identify usage pattern
* Filter logs by API Keys

#### When not use API Keys
* Identify individual users
* Secure authorization
* identify the creators of a project

#### Handling API Keys
* Do not embed API keys directly in code. Instead of embedding your API keys in your applications, store them in environment variables or in files outside of your application's source tree.


### OAuth

## References
[3-common-methods-api-authentication-explained/](https://nordicapis.com/3-common-methods-api-authentication-explained/)
[when-why-api-key#security_of_api_keys](https://cloud.google.com/endpoints/docs/openapi/when-why-api-key#security_of_api_keys)
[authentication - api-keys](https://cloud.google.com/docs/authentication/api-keys)

## Authorization
### Role-Based Access Control
### Attribute-Based Access Control
### Delegated Access Control with OAuth 2.0


