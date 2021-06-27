# OAuth2 simplified

The OAuth 2 spec can be a bit confusing to read, so I've written this post to help describe the terminology in a simplified format. The core spec leaves many decisions up to the implementer, often based on security tradeoffs of the implementation. Instead of describing all possible decisions that need to be made to successfully implement OAuth 2, this post makes decisions that are appropriate for most implementations.

### Roles

The Third-Party Application: "Client"

The client is the application that is attempting to get access to the user's account. It needs to get permission from the user before it can do so.
The API: "Resource Server"

The resource server is the API server used to access the user's information.
The Authorization Server

This is the server that presents the interface where the user approves or denies the request. In smaller implementations, this may be the same server as the API server, but larger scale deployments will often build this as a separate component.
The User: "Resource Owner"

The resource owner is the person who is giving access to some portion of their account.

### Creating an App

Before you can begin the OAuth process, you must first register a new app with the service. When registering a new app, you usually register basic information such as application name, website, a logo, etc. In addition, you must register a redirect URI to be used for redirecting users to for web server, browser-based, or mobile apps.

## Authorization

The first step of OAuth 2 is to get authorization from the user. For browser-based or mobile apps, this is usually accomplished by displaying an interface provided by the service to the user.

OAuth 2 provides several "grant types" for different use cases. The grant types defined are:

1. Authorization Code for apps running on a web server, browser-based and mobile apps.

2. Password for logging in with a username and password (only for first-party apps).

3. Client credentials for application access without a user present.

4. Implicit was previously recommended for clients without a secret, but has been superseded by using the Authorization Code grant with PKCE.

## Build a Node API with OAuth

Build Your REST API with Node, Express, Sequelize, and Finale

Now that you have a working Express server, you can add a REST API. This is actually much simpler than you might think. The easiest way I’ve seen is by using Sequelize to define your database schema, and Finale to create some REST API endpoints with near-zero boilerplate.

You’ll need to add those dependencies to your project. Sequelize also needs to know how to communicate with the database. For now, use SQLite as it will get us up and running quickly.

npm install sequelize@6.6.2 finale-rest@1.0.6 sqlite3@5.0.2

Create a new file database.js with the following code. I’ll explain each part in more detail below.

        database.js

        const Sequelize = require('sequelize')
        const finale = require('finale-rest')

        const database = new Sequelize({
        dialect: 'sqlite',
        storage: './test.sqlite'
        })

        const Part = database.define('parts', {
        partNumber: Sequelize.STRING,
        modelNumber: Sequelize.STRING,
        name: Sequelize.STRING,
        description: Sequelize.TEXT
        })

        const initializeDatabase = async (app) => {
        finale.initialize({ app, sequelize: database })

        finale.resource({
            model: Part,
            endpoints: ['/parts', '/parts/:id']
        })

        await database.sync()
        }

        module.exports = initializeDatabase

Now you just need to import that file into your main app and run the initialization function. Make the following additions to your index.js file.

        index.js

        @@ -2,10 +2,13 @@ const express = require('express')
        const bodyParser = require('body-parser')
        const { promisify } = require('util')

        +const initializeDatabase = require('./database')
        +
        const app = express()
        app.use(bodyParser.json())

        const startServer = async () => {
        +  await initializeDatabase(app)
        const port = process.env.SERVER_PORT || 3000
        await promisify(app.listen).bind(app)(port)
        console.log(`Listening on port ${port}`)

You can now test for syntax errors and run the app if everything seems good:

        $ npm test && node .

        > rest-api@1.0.0 test /Users/bmk/code/okta/apps/rest-api
        > standard

        Executing (default): CREATE TABLE IF NOT EXISTS `parts` (`id` INTEGER PRIMARY KEY AUTOINCREMENT, `partNumber` VARCHAR(255), `modelNu
        mber` VARCHAR(255), `name` VARCHAR(255), `description` TEXT, `createdAt` DATETIME NOT NULL, `updatedAt` DATETIME NOT NULL);
        Executing (default): PRAGMA INDEX_LIST(`parts`)
        Listening on port 3000

In another terminal, you can test that this is actually working (to format the JSON response I use a json CLI, installed globally using npm install --global json):

        $ curl localhost:3000/parts
        []

        $ curl localhost:3000/parts -X POST -d '{
        "partNumber": "abc-123",
        "modelNumber": "xyz-789",
        "name": "Alphabet Soup",
        "description": "Soup with letters and numbers in it"
        }' -H 'content-type: application/json' -s0 | json
        {
        "id": 1,
        "partNumber": "abc-123",
        "modelNumber": "xyz-789",
        "name": "Alphabet Soup",
        "description": "Soup with letters and numbers in it",
        "updatedAt": "2018-08-16T02:22:09.446Z",
        "createdAt": "2018-08-16T02:22:09.446Z"
        }

        $ curl localhost:3000/parts -s0 | json
        [
        {
            "id": 1,
            "partNumber": "abc-123",
            "modelNumber": "xyz-789",
            "name": "Alphabet Soup",
            "description": "Soup with letters and numbers in it",
            "createdAt": "2018-08-16T02:22:09.446Z",
            "updatedAt": "2018-08-16T02:22:09.446Z"
        }
        ]

## OAuth wiki

OAuth is an open standard for access delegation, commonly used as a way for Internet users to grant websites or applications access to their information on other websites but without giving them the passwords.This mechanism is used by companies such as Amazon, Google, Facebook, Microsoft and Twitter to permit the users to share information about their accounts with third party applications or websites.

Generally, OAuth provides clients a "secure delegated access" to server resources on behalf of a resource owner. It specifies a process for resource owners to authorize third-party access to their server resources without providing credentials. Designed specifically to work with Hypertext Transfer Protocol (HTTP), OAuth essentially allows access tokens to be issued to third-party clients by an authorization server, with the approval of the resource owner. The third party then uses the access token to access the protected resources hosted by the resource server.

OAuth is a service that is complementary to and distinct from OpenID. OAuth is unrelated to OATH, which is a reference architecture for authentication, not a standard for authorization. However, OAuth is directly related to OpenID Connect (OIDC), since OIDC is an authentication layer built on top of OAuth 2.0. OAuth is also unrelated to XACML, which is an authorization policy standard. OAuth can be used in conjunction with XACML, where OAuth is used for ownership consent and access delegation whereas XACML is used to define the authorization policies (e.g., managers can view documents in their region).

## OAuth 2.0

OAuth 2.0 is not backwards compatible with OAuth 1.0. OAuth 2.0 provides specific authorization flows for web applications, desktop applications, mobile phones, and smart devices. The specification and associated RFCs are developed by the IETF OAuth WG; the main framework was published in October 2012.

Facebook's Graph API only supports OAuth 2.0.Google supports OAuth 2.0 as the recommended authorization mechanism for all of its APIs.[10] Microsoft also supports OAuth 2.0 for various APIs and its Azure Active Directory service,which is used to secure many Microsoft and third party APIs.

The OAuth 2.0 Framework and Bearer Token Usage were published in October 2012.

The OAuth 2.1 Authorization Framework is in draft stage.

## OAuth 2.0

In January 2013, the Internet Engineering Task Force published a threat model for OAuth 2.0.Among the threats outlined is one called "Open Redirector"; in early 2014, a variant of this was described under the name "Covert Redirect" by Wang Jing.

OAuth 2.0 has been analyzed using formal web protocol analysis. This analysis revealed that in setups with multiple authorization servers, one of which is behaving maliciously, clients can become confused about the authorization server to use and may forward secrets to the malicious authorization server (AS Mix-Up Attack).This prompted the creation of a new best current practice internet draft that sets out to define a new security standard for OAuth 2.0.Assuming a fix against the AS Mix-Up Attack in place, the security of OAuth 2.0 has been proven under strong attacker models using formal analysis.

One implementation of OAuth 2.0 with numerous security flaws has been exposed.

In April and May 2017, about one million users of Gmail (less than 0.1% of users as of May 2017) were targeted by an OAuth-based phishing attack, receiving an email purporting to be from a colleague, employer or friend wanting to share a document on Google Docs.Those who clicked on the link within the email were directed to sign in and allow a potentially malicious third-party program called "Google Apps" to access their "email account, contacts and online documents".Within "approximately one hour",[25] the phishing attack was stopped by Google, who advised those who had given "Google Apps" access to their email to revoke such access and change their passwords.

#### References

- OAuth2 simplified  [Read the full article here](https://aaronparecki.com/oauth-2-simplified/)

- OAuth [OAuth wiki](https://en.wikipedia.org/wiki/OAuth)

- Build a Node API with OAuth [Read the full article here](https://developer.okta.com/blog/2018/08/21/build-secure-rest-api-with-node)
- What is OAuth Really All About? [Check it out](https://www.youtube.com/watch?v=t4-416mg6iU)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
