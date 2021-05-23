# Review, Research, and DiscussionReview, Research, and Discussion

- ***Write the following steps in the correct order:***

1. Register your application to get a client_id and client_secret
2. Ask the client if they want to sign in via a third party
3. Redirect to a third party authentication endpoint
4. Receive authorization code
5. Make a request to a third-party API endpoint
6. Receive access token
7. Make a request to the access token endpoint

## Term

- Client ID: A Client ID is an identifier associated with an application that assists with client / server OAuth 2.0 authentication for ArcGIS client APIs . Developers create a client ID by defining an application on their developer dashboard.

- Client Secret: A client secret is a secret known only to your application and the authorization server. It protects your resources by only granting tokens to authorized requestors. Protect your client secrets and never include them in mobile or browser-based apps.

- Authentication Endpoint: Endpoint authentication is an authentication mechanism used to verify the identity of a network's external or remote connecting device. These endpoint devices include laptops, smartphones, tablets, and servers. This method ensures that only valid or authorized endpoint devices are connected to a network.

- Access Token Endpoint: The token endpoint is where apps make a request to get an access token for a user. This section describes how to verify token requests and how to return the appropriate response and errors. Authorization Code. Password Grant. Client Credentials.

- API Endpoint: In simple terms, an API endpoint is the point of entry in a communication channel when two systems are interacting. It refers to touchpoints of the communication between an API and a server. ... An API endpoint is basically a fancy word for a URL of a server or service.

- Authorization Code: The authorization code is a temporary code that the client will exchange for an access token. The code itself is obtained from the authorization server where the user gets a chance to see what the information the client is requesting, and approve or deny the request.

- Access Token: An access token is an object encapsulating the security identity of a process or thread. A token is used to make security decisions and to store tamper-proof information about some system entity.

## Preview

1. Which 3 things had you heard about previously and now have better clarity on?

- Testing.
- Database.
- Query string.

2. Which 3 things are you hoping to learn more about in the upcoming lecture/demo?

- Client Secret.
- Access Token Endpoint.
- JWTs.

3. What are you most excited about trying to implement or see how it works?

- JWTs.

## Introduction to JSON Web Tokens

### What is JSON Web Token?

- JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.

Although JWTs can be encrypted to also provide secrecy between parties, we will focus on signed tokens. Signed tokens can verify the integrity of the claims contained within it, while encrypted tokens hide those claims from other parties. When tokens are signed using public/private key pairs, the signature also certifies that only the party holding the private key is the one that signed it.

### When should you use JSON Web Tokens?

Here are some scenarios where JSON Web Tokens are useful:

- Authorization: This is the most common scenario for using JWT. Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token. Single Sign On is a feature that widely uses JWT nowadays, because of its small overhead and its ability to be easily used across different domains.

- Information Exchange: JSON Web Tokens are a good way of securely transmitting information between parties. Because JWTs can be signed—for example, using public/private key pairs—you can be sure the senders are who they say they are. Additionally, as the signature is calculated using the header and the payload, you can also verify that the content hasn't been tampered with.

### What is the JSON Web Token structure?

In its compact form, JSON Web Tokens consist of three parts separated by dots (.), which are:

1. Header
2. Payload
3. Signature

### How do JSON Web Tokens work?

In authentication, when the user successfully logs in using their credentials, a JSON Web Token will be returned. Since tokens are credentials, great care must be taken to prevent security issues. In general, you should not keep tokens longer than required.

You also should not store sensitive session data in browser storage due to lack of security.

Whenever the user wants to access a protected route or resource, the user agent should send the JWT, typically in the Authorization header using the Bearer schema. The content of the header should look like the following:

        Authorization: Bearer <token>

This can be, in certain cases, a stateless authorization mechanism. The server's protected routes will check for a valid JWT in the Authorization header, and if it's present, the user will be allowed to access protected resources. If the JWT contains the necessary data, the need to query the database for certain operations may be reduced, though this may not always be the case.

If the token is sent in the Authorization header, Cross-Origin Resource Sharing (CORS) won't be an issue as it doesn't use cookies.

### Are JWTs Secure?

JWTs can be either signed, encrypted or both. If a token is signed, but not encrypted, everyone can read its contents, but when you don't know the private key, you can't change it. Otherwise, the receiver will notice that the signature won't match anymore.

Answer to your comment: I'm not sure if I understand your comment the right way. Just to be sure: do you know and understand digital signatures? I'll just briefly explain one variant (HMAC, which is symmetrical, but there are many others).

Let's assume Alice wants to send a JWT to Bob. They both know some shared secret. Mallory doesn't know that secret, but wants to interfere and change the JWT. To prevent that, Alice calculates Hash(payload + secret) and appends this as signature.

When receiving the message, Bob can also calculate Hash(payload + secret) to check whether the signature matches. If however, Mallory changes something in the content, she isn't able to calculate the matching signature (which would be Hash(newContent + secret)). She doesn't know the secret and has no way of finding it out. This means if she changes something, the signature won't match anymore, and Bob will simply not accept the JWT anymore.

Let's suppose, I send another person the message {"id":1} and sign it with Hash(content + secret). (+ is just concatenation here). I use the SHA256 Hash function, and the signature I get is: 330e7b0775561c6e95797d4dd306a150046e239986f0a1373230fda0235bda8c. Now it's your turn: play the role of Mallory and try to sign the message {"id":2}. You can't because you don't know which secret I used. If I suppose that the recipient knows the secret, he CAN calculate the signature of any message and check if it's correct.

**References:**

- JWTs Explained [Check it out](https://www.youtube.com/watch?v=926mknSW9Lo)

- Intro to JWT [Read the full article here](https://jwt.io/introduction/)

- Are JWTs Secure? [Read the full article here](https://stackoverflow.com/questions/27301557/if-you-can-decode-jwt-how-are-they-secure)

- npm jsonwebtoken docs [Check it out](https://www.npmjs.com/package/jsonwebtoken)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
