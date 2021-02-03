# OpenID Connect & OAuth2

The OpenId Connect is an identity layer ontop the OAuth2 protocol. I find that documentation often intermixes the two, and these notes mostly covers the OpenID spec.

## Flows

Flows are also called grant types which is the process for how a client gets an access token from the auth server. 

The **Authorization code** is mostly used for server-side and mobile web apps. **Client credentials** is used for server-to-server auth, and typically the client application has the credientials it uses for authentication. **Implicit** the client gets the access token directly when credentials cannot be stored because they are easily access by a third party. Used when your application doesn't have a server component.



**Flow types**

- `authorizationCode` (previously `accessCode`)
- `implicit`
- `password`
- `clientCredentials` (previously `application`)


**OpenID Connect Discovery**

OpenID Connect defines a discovery mechanism, called OpenID Connect Discovery, where an OpenID server publishes its metadata at a well-known URL [.well-known/openid-configuration](https://auth0.auth0.com/.well-known/openid-configuration). This was added to the OAuth2 protocol.


**Scope**

Scope is used to limit an application's access to a user's account. The user is often presented with the scopes to provide consent. The application has to determine how it access the user's information. Using scopes is optional. 

**ID Token schema**

Bolded are required.

**iss** - Issuer Identifier which is a case sensitive URL using https. type: url

**sub** - Subject Identifier which is a unique and never reassigned identifer stored within the Issuer for the End-User. type: string

**aud** - Audience the token is intended for which must contain the Relying Party as an audience value. It may container other audiences. type: array of strings

**exp** - Expiration time at which the token must not be accepted for processing. type: unixtime number

**iat** - Time when the JWT was issued. type: unixtime number

auth_time -  When the end-user authentication occured. type: unixtime number

nonce - Used to prevent replay access, as the clients much verify the nonce claim value. type: string

acr - Authentication Context Class Reference allows you to specific a long-lived session such as an expires weekly cookie, but then requires you to re-authenticate to change your password, add a bank account, send money, etc.

amr - Authentication Methods References values which might indicate authentication methods such as: password and/or OTP. type: json array of strings.

azp - Authorized Party is the party to which the token was issued. type: StringOrURI value



Glossary:

- Client: Usually a end-user authenticating from a web browser or mobile app.
- Authorization Server: OpenID SSO authentication provider such as Google, Twitter, Auth0, Okta. Often reference as Issuer.
- Relay Server: Typically the web application you are trying to access. 

When I use my Firefox browser(Client) to log into StackOverflow.com (Relay Server), I'm logging in with my Google Account (Issuer).

- Bearer Authentication (aka token authentication) `Authorization: Bearer <token>`


Sources:
 - [Swagger Auth Overview](https://swagger.io/docs/specification/authentication/)
 - [OpenID Spec](https://openid.net/specs/openid-connect-core-1_0.html)
 - [OpenID Primer from Okta](https://developer.okta.com/blog/2017/07/25/oidc-primer-part-1)