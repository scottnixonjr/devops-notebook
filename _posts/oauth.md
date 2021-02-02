# OAuth

## Flows

Flows are also called grant types which is the process for how a client gets an access token from the auth server. 

The **Authorization code** is mostly used for server-side and mobile web apps. **Client credentials** is used for server-to-server auth, and typically the client application has the credientials it uses for authentication. **Implicit** the client gets the access token directly when credentials cannot be stored because they are easily access by a third party. Used when your application doesn't have a server component.



**Flow types**

- `authorizationCode` (previously `accessCode`)
- `implicit`
- `password`
- `clientCredentials` (previously `application`)


OpenID Connect defines a discovery mechanism, called OpenID Connect Discovery, where an OpenID server publishes its metadata at a well-known URL [.well-known/openid-configuration](https://auth0.auth0.com/.well-known/openid-configuration)


**Scope**

Scope is used to limit an application's access to a user's account. The user is often presented with the scopes to provide consent. The application has to determine how it access the user's information. Using scopes is optional. 


Glossary:

- Bearer Authentication (aka token authentication) `Authorization: Bearer <token>`


Sources:
 - [Swagger](https://swagger.io/docs/specification/authentication/)