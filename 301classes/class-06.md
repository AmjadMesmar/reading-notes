
# What Is Node and When Should I Use It?

- ***What Is Node.js?***
There are plenty of definitions to be found online. Let’s take a look at a couple of the more popular ones. This is what the project’s home page has to say:

    Node.js® is a JavaScript runtime built on Chrome’s V8 JavaScript engine.

And this is what Stack Overflow has to offer:

    Node.js is an event-based, non-blocking, asynchronous I/O runtime that uses Google’s V8 JavaScript engine and libuv library.

Hmmm, “event-based”, “non-blocking”, “asynchronous I/O” — that’s quite a lot to digest in one go. So let’s approach this from a different angle and begin by focusing on the other detail that both descriptions mention — the V8 JavaScript engine.

- ***How Do I Install Node.js?***

In this next section, we’ll install Node and write a couple of simple programs. We’ll also look at npm, a package manager that comes bundled with Node.

- ***Node Binaries vs Version Manager***

Many websites will recommend that you head to the official Node download page and grab the Node binaries for your system. While that works, I would suggest that you use a version manager instead. This is a program that allows you to install multiple versions of Node and switch between them at will. There are various advantages to using a version manager. For example, it negates potential permission issues when using Node with npm and lets you set a Node version on a per-project basis.

- ***“Hello, World!” the Node.js Way***

You can check that Node is installed on your system by opening a terminal and typing node -v. If all has gone well, you should see something like v12.14.1 displayed. This is the current LTS version at the time of writing.

Next, create a new file hello.js and copy in the following code:

        console.log("Hello, World!");

This uses Node’s built-in console module to display a message in a terminal window. To run the example, enter the following command:

        node hello.js

If Node.js is configured properly, “Hello, World!” will be displayed.

- ***Installing a Package Globally***

Open your terminal and type the following:

        npm install -g jshint

This will install the jshint package globally on your system. We can use it to lint the index.js file from the previous example:

        jshint index.js

You should now see a number of ES6-related errors. If you want to fix them up, add /* jshint esversion: 6 */ to the top of the index.js file, re-run the command and linting should pass.

If you’d like a refresher on linting, see A Comparison of JavaScript Linting Tools.

- ***Installing a Package Locally***

We can also install packages locally to a project, as opposed to globally, on our system. Create a test folder and open a terminal in that directory. Next type this:

        npm init -y

This will create and auto-populate a package.json file in the same folder. Next, use npm to install the lodash package and save it as a project dependency:

        npm install lodash --save

Create a file named test.js and add the following:

        const _ = require('lodash');

        const arr = [0, 1, false, 2, '', 3];
        console.log(_.compact(arr));

Finally, run the script using node test.js. You should see [ 1, 2, 3 ] output to the terminal.

**References:**

- Common Responsive Layouts with CSS Grid (and some without!) [Read the full article here](https://www.sitepoint.com/an-introduction-to-node-js/)

## [Main page](https://amjadmesmar.github.io/reading-notes/)