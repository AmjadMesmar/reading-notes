
# Using the API

## Introduction

This document is intended for developers who want to write applications that can interact with the Books API. Google Books has a mission to digitize the world's book content and make it more discoverable on the Web. The Books API is a way to search and access that content, as well as to create and view personalization around that content.

If you're unfamiliar with Google Books concepts, you should read Getting Started before starting to code.
Authorizing requests and identifying your application

Every request your application sends to the Books API needs to identify your application to Google. There are two ways to identify your application: using an OAuth 2.0 token (which also authorizes the request) and/or using the application's API key. Here's how to determine which of those options to use:

- If the request requires authorization (such as a request for an individual's private data), then the application must provide an OAuth 2.0 token with the request. The application may also provide the API key, but it doesn't have to.

- If the request doesn't require authorization (such as a request for public data), then the application must provide either the API key or an OAuth 2.0 token, or both—whatever option is most convenient for you.

- **About authorization protocols**

Your application must use OAuth 2.0 to authorize requests. No other authorization protocols are supported. If your application uses Google Sign-In, some aspects of authorization are handled for you.

- **Authorizing requests with OAuth 2.0**

Requests to the Books API for non-public user data must be authorized by an authenticated user.

The details of the authorization process, or "flow," for OAuth 2.0 vary somewhat depending on what kind of application you're writing. The following general process applies to all application types:

1. When you create your application, you register it using the Google API Console. Google then provides information you'll need later, such as a client ID and a client secret.

2. Activate the Books API in the Google API Console. (If the API isn't listed in the API Console, then skip this step.)

3. When your application needs access to user data, it asks Google for a particular scope of access.

4. Google displays a consent screen to the user, asking them to authorize your application to request some of their data.

5. If the user approves, then Google gives your application a short-lived access token.

6. Your application requests user data, attaching the access token to the request.

7. If Google determines that your request and the token are valid, it returns the requested data.

Some flows include additional steps, such as using **refresh tokens** to acquire new access tokens. For detailed information about flows for various types of applications, see Google's OAuth 2.0 documentation.

Here's the OAuth 2.0 scope information for the Books API:

        https://www.googleapis.com/auth/books

## How To Use EJS to Template Your Node Application

- **Setting up the Demo App**

We will be making two pages for our application with one page with full width and the other with a sidebar.

Get the code: You can find a git repo of the complete demo code on GitHub here
File Structure

Here are the files we’ll need for our application. We’ll do our templating inside of the views folder and the rest is pretty standard Node practices.

        - views
        ----- partials
        ---------- footer.ejs
        ---------- head.ejs
        ---------- header.ejs
        ----- pages
        ---------- index.ejs
        ---------- about.ejs
        - package.json
        - server.js

- package.json will hold our Node application information and the dependencies we need (express and EJS). server.js will hold our Express server setup, configuration. We’ll define our routes to our pages here.

- **Node Setup**

Let’s go into our package.json file and set up our project there.
package.json

                     package.json

        {
          "name": "node-ejs",
          "main": "server.js",
          "dependencies": {
            "ejs": "^3.1.5",
            "express": "^4.17.1"
          }
        }

All we will need is Express and EJS. Now we have to install the dependencies we just defined. Go ahead and run:

     npm install

With all of our dependencies installed, let’s configure our application to use EJS and set up our routes for the two pages we need: the index page (full width) and the about page (sidebar). We will do all of this inside our server.js file.

                            server.js

        // load the things we need
        var express = require('express');
        var app = express();

        // set the view engine to ejs
        app.set('view engine', 'ejs');

        // use res.render to load up an ejs view file

        // index page
        app.get('/', function(req, res) {
            res.render('pages/index');
        });

        // about page
        app.get('/about', function(req, res) {
            res.render('pages/about');
        });

        app.listen(8080);
        console.log('8080 is the magic port');

- Here we define our application and set it to show on port 8080. We also have to set EJS as the view engine for our Express application using app.set('view engine', 'ejs');. Notice how we send a view to the user by using res.render(). It is important to note that res.render() will look in a views folder for the view. So we only have to define pages/index since the full path is views/pages/index.


Start Up our Server

Go ahead and start the server using:

    node server.js

 

Now we can see our application in the browser at http://localhost:8080 and http://localhost:8080/about. Our application is set up and we have to define our view files and see how EJS works there.
Create the EJS Partials

Like a lot of the applications we build, there will be a lot of code that is reused. We’ll call those partials and define three files we’ll use across all of our site: head.ejs, header.ejs, and footer.ejs. Let’s make those files now.

                        views/partials/head.ejs

        <meta charset="UTF-8">
        <title>EJS Is Fun</title>

        <!-- CSS (load bootstrap from a CDN) -->
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/4.5.2/css/bootstrap.min.css">
        <style>
            body { padding-top:50px; }
        </style>


              views/partials/header.ejs

        <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <a class="navbar-brand" href="/">EJS Is Fun</a>
        <ul class="navbar-nav mr-auto">
            <li class="nav-item">
            <a class="nav-link" href="/">Home</a>
            </li>
            <li class="nav-item">
            <a class="nav-link" href="/about">About</a>
            </li>
        </ul>
        </nav>


                views/partials/footer.ejs

        <p class="text-center text-muted">© Copyright 2020 The Awesome People</p>


### REFERENCE

- Watch EJS tutorial from WalkThroughCode on YouTube, Videos 1-5 [Check it out](https://www.youtube.com/playlist?list=PL7sCSgsRZ-slYARh3YJIqPGZqtGVqZRGt)

- Google Books API Docs [Check it out](https://developers.google.com/books/docs/v1/using#WorkingVolumes)

- EJS Docs [Check it out](https://ejs.co/)

- LEJS Tutorial [Read the full article here](https://visionmedia.github.io/superagent/)

- Source Code for the EJS Tutorial [Check it out](https://github.com/scotch-io/node-ejs)

## [Main page](https://amjadmesmar.github.io/reading-notes/)