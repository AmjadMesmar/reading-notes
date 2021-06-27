# Review, Research, and Discussion

1. When is Basic Authorization used vs. Bearer Authorization?

The Basic and Digest authentication schemes are dedicated to the authentication using a username and a secret.

The Bearer authentication scheme is dedicated to the authentication using a token and is described by the RFC6750. Even if this scheme comes from an OAuth2 specification, you can still use it in any other context where tokens are exchange between a client and a server.

Concerning the JWT authentication and as it is a token, the best choice is the Bearer authentication scheme. Nevertheless, nothing prevent you from using a custom scheme that could fit on your requirements.

2. What does the JSON Web Token package do?

JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed.

3. What considerations should we make when creating and storing a SECRET?

- Don't store secrets in GitHub repositories

- Don’t share your secrets unencrypted.

- Always Restrict API access and permissions.

## Document the following Vocabulary Terms

- ***encryption***: In cryptography, encryption is the process of encoding information. This process converts the original representation of the information, known as plaintext, into an alternative form known as ciphertext. Ideally, only authorized parties can decipher a ciphertext back to plaintext and access the original information.

- ***token***: In programming, a token is a single element of a programming language. There are five categories of tokens: 1) constants, 2) identifiers, 3) operators, 4) separators, and 5) reserved words. ... Operators, such as +, -, *, and /, are also tokens of nearly all programming languages.

- ***bearer***: The Bearer Token is created for you by the Authentication server. When a user authenticates your application (client) the authentication server then goes and generates for you a Token. Bearer Tokens are the predominant type of access token used with OAuth 2.0. ... You use the bearer token to get a new Access token.

- ***secret***: is unique to the client application on that authorization server. ... When a resource owner has successfully authorized the client application via the authorization server, the resource owner is redirected back to the client application, to the redirect URI.

- ***JSON Web Token***: JSON Web Token is a proposed Internet standard for creating data with optional signature and/or optional encryption whose payload holds JSON that asserts some number of claims. The tokens are signed either using a private secret or a public/private key.

### 5 steps to simple role-based access control (RBAC)

RBAC is the idea of assigning system access to users based on their role in an organization. It's important to remember that not every employee needs a starring role.

Despite all of the advanced attack scenarios we face in cybersecurity today, it seems like we continue to shoot ourselves in the proverbial feet with the simple things.

Why do we find something as seemingly simple as access control to be such a challenge? Perhaps it is because it only seems simple. As an example, consider a company with just 20 employees and 5 systems. Let's also assume that for each system, a given user might need to use it only to read files, for read/writing of files, for administrative access, or no access at all. The number of possible permutations of access settings in such a small environment is huge.

Add to the problem the fact that in a typical smaller company, management of access rights is casual at best, even "one size fits all" in some cases. It seems that this simple problem is not so simple at all. Yet, if we can't get this right, our chance of having even reasonably secure systems is pretty small.

The solution to this problem is not new. It dates back to the 1970s, long before information security was on anyone’s radar. The approach is called role-based access control (RBAC). According to a National Institute of Standards and Technology (NIST) document, the first formal RBAC model was proposed in 1992. Thus, we have been sitting on a strong approach to this problem for many years.

### What is RBAC?

RBAC is nothing more than the idea of assigning system access to users based on their role within an organization. The system needs of a given workforce are analyzed, with users grouped into roles based on common job responsibilities and system access needs. Access is then assigned to each person based strictly on their role assignment. With tight adherence to access requirements established for each role, access management becomes much easier.

The question therefore is why, with an achievable and time-honored approach, we can’t seem to get a handle on access control. We are certainly being pushed in that direction of RBAC, with all of the major standards, including PCI DSS, HIPAA and Gramm-Leach-Bliley all requiring some form of it.

### Role-based access control

In computer systems security, role-based access control (RBAC) or role-based security is an approach to restricting system access to authorized users. It is used by the majority of enterprises with more than 500 employees, and can implement mandatory access control (MAC) or discretionary access control (DAC).

Role-based access control (RBAC) is a policy-neutral access-control mechanism defined around roles and privileges. The components of RBAC such as role-permissions, user-role and role-role relationships make it simple to perform user assignments. A study by NIST has demonstrated that RBAC addresses many needs of commercial and government organizations.[5] RBAC can be used to facilitate administration of security in large organizations with hundreds of users and thousands of permissions. Although RBAC is different from MAC and DAC access control frameworks, it can enforce these policies without any complication.

## Design

Within an organization, roles are created for various job functions. The permissions to perform certain operations are assigned to specific roles. Members or staff (or other system users) are assigned particular roles, and through those role assignments acquire the permissions needed to perform particular system functions. Since users are not assigned permissions directly, but only acquire them through their role (or roles), management of individual user rights becomes a matter of simply assigning appropriate roles to the user's account; this simplifies common operations, such as adding a user, or changing a user's department.

Role based access control interference is a relatively new issue in security applications, where multiple user accounts with dynamic access levels may lead to encryption key instability, allowing an outside user to exploit the weakness for unauthorized access. Key sharing applications within dynamic virtualized environments have shown some success in addressing this problem.

Three primary rules are defined for RBAC:

Role assignment: A subject can exercise a permission only if the subject has selected or been assigned a role.

Role authorization: A subject's active role must be authorized for the subject. With rule 1 above, this rule ensures that users can take on only roles for which they are authorized.

Permission authorization: A subject can exercise a permission only if the permission is authorized for the subject's active role. With rules 1 and 2, this rule ensures that users can exercise only permissions for which they are authorized.

#### References

- RBAC tutorial[Check it out](https://www.youtube.com/watch?v=C4NP8Eon3cA)

- 5 steps to simple role-based access control (RBAC) [Read the full article here](https://www.csoonline.com/article/3060780/5-steps-to-simple-role-based-access-control.html)

- Role-based access control [Read the full article here](https://en.wikipedia.org/wiki/Role-based_access_control)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
