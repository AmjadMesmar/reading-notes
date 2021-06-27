# Review, Research, and Discussion

1. Explain what a “Singleton” is (in Computer Science terms):
The purpose of the singleton class is to control object creation, limiting the number of objects to only one. The singleton allows only one entry point to create the new instance of the clas.

2. Explain how the Singleton pattern can be used with Node modules, specifically with classes:

### How to create Singleton Instance in Node.js?

In the last Section we took a look at how creating multiple instances of the logger class can cause problems within our application. In this section we’re going to go ahead and fix those problems by implementing a singleton. So logger.js file let’s go ahead and modify this file to export a singleton instead of a logger. So on line 17 I’m just going to come in here and add a new class called singleton. So this class is only going to allow us to create one instance of the logger. Anytime we need that instance we’re going to retrieve it through a get instance method.

So let’s go ahead and add a constructor to our singleton class. And what we want to do within this constructor is we want to check and see if an instance has already been created. So I’m going to save the instance directly to the class. So if there’s not a singleton instance then we want to create one. So if we don’t have one then the singleton instance will equal new logger. So that’s our singleton. And it will only allow us to create one instance whenever we instantiate this singleton class.

So the next thing we’re going to do for a classical singleton is actually return that instance using a get instance method. And what we can do within this method is return our singleton instance. There we go. So this class only allows us to instantiate one logger and then using the get instance method we can return that logger to any file that wants to use it.
3. If you were tasked with building a middleware system like Express uses, what approach might you take to construct/operate it?

1. Create that middleware file and write the middleare function, then export it.

2. Import the middleware file inside the js file you want to use in.

## Document

- Router Middleware: Router is one of those middleware, what it does actualy is to take the original request, and forward it to a sub handler according to the path example : "/home" for a GET request is mapped to function getHome that handle it and eventually send a response to the client on the behalf of the original handler.

- Dynamic Module Loading: Dynamic loading is a mechanism by which a computer program can, at run time, load a library (or other binary) into memory, retrieve the addresses of functions and variables contained in the library, execute those functions or access those variables, and unload the library from memory. It is one of the 3 mechanisms by which a computer program can use some other software; the other two are static linking and dynamic linking. Unlike static linking and dynamic linking, dynamic loading allows a computer program to start up in the absence of these libraries, to discover available libraries, and to potentially gain additional functionality.

- Singleton Pattern: In software engineering, the singleton pattern is a software design pattern that restricts the instantiation of a class to one "single" instance. This is useful when exactly one object is needed to coordinate actions across the system. The term comes from the mathematical concept of a singleton.

- CRUD -> REST Method Matches:

        Create = PUT with a new URI
        POST to a base URI returning a newly created URI
    Explain what a “Singleton” is (in Computer Science terms)
    Explain how the Singleton pattern can be used with Node modules, specifically with classes
    If you were tasked with building a middleware system like Express uses, what approach might you take to construct/operate it?

        Delete = DELETE

- Mock Testing: Mock testing is an approach to unit testing that lets you make assertions about how the code under test is interacting with other system modules. In mock testing, the dependencies are replaced with objects that simulate the behaviour of the real ones.

## Securing Passwords with Bcrypt Hashing Function

### PROBLEMS WITH CRYPTOGRAPHIC HASH ALGORITHM

Brute Force attack: Hashes can't be reversed, so instead of reversing the hash of the password, an attacker can simply keep trying different inputs until he does not find the right now that generates the same hash value, called brute force attack.

- Hash Collision attack: Hash functions have infinite input length and a predefined output length, so there is inevitably going to be the possibility of two different inputs that produce the same output hash. MD5, SHA1, SHA2 are vulnerable to Hash Collision Attack i.e. two input strings of a hash function that produce the same hash result.

Salting your password may foil dictionary attacks, but an attacker can still use a wordlist to crack the hashes. So, what exactly could be a good for securing your passwords with hashing?

BCrypt, IT's SLOW AND STRONG AS HELL
To overcome such issues, we need algorithms which can make the brute force attacks slower and minimize the impact. Such algorithms are PBKDF2 and BCrypt, both of these algorithms use a technique called Key Stretching.

Bcrypt is an adaptive hash function based on the Blowfish symmetric block cipher cryptographic algorithm and introduces a work factor (also known as security factor), which allows you to determine how expensive the hash function will be.

## Basic access authentication

In the context of an HTTP transaction, basic access authentication is a method for an HTTP user agent (e.g. a web browser) to provide a user name and password when making a request. In basic HTTP authentication, a request contains a header field in the form of Authorization: Basic <credentials>, where credentials is the Base64 encoding of ID and password joined by a single colon :.

It is specified in RFC 7617 from 2015, which obsoletes RFC 2617 from 1999.

## Protocol

### Server side

When the server wants the user agent to authenticate itself towards the server, the server must respond appropriately to unauthenticated requests.

To unauthenticated requests, the server should return a response which contains a HTTP 401 Unauthorized status line[5] and a WWW-Authenticate header field.[6]

The WWW-Authenticate header field for basic authentication is constructed as following:

1. WWW-Authenticate: Basic realm="User Visible Realm"

2. The server may choose to include the charset parameter from RFC 7617:[1]

3. WWW-Authenticate: Basic realm="User Visible Realm", charset="UTF-8"

4. This parameter indicates that the server expects the client to use UTF-8 for encoding username and password (see below).

### Client side

When the user agent wants to send authentication credentials to the server, it may use the Authorization header field.

- The Authorization header field is constructed as follows:[7]

- The username and password are combined with a single colon (:). This means that the username itself cannot contain a colon.

- The resulting string is encoded into an octet sequence. The character set to use for this encoding is by default unspecified, as long as it is compatible with US-ASCII, but the server may suggest use of UTF-8 by sending the charset parameter.

- The resulting string is encoded using a variant of Base64 (+/ and with padding).

- The authorization method and a space (e.g. "Basic ") is then prepended to the encoded string.

For example, if the browser uses Aladdin as the username and open sesame as the password, then the field's value is the Base64 encoding of Aladdin:open sesame, or QWxhZGRpbjpvcGVuIHNlc2FtZQ==. Then the Authorization header field will appear as:

        Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==

#### References

- Securing Passwords. [Read the full article here](https://thehackernews.com/2014/04/securing-passwords-with-bcrypt-hashing.html)

- Basic Auth. [Read the full article here](https://en.wikipedia.org/wiki/Basic_access_authentication)

- bcrypt docs. [Check it out](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)

- OWASP auth cheatsheet. [Check it out](https://www.npmjs.com/package/bcrypt)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
