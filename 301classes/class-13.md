# Sending form data

Once the form data has been validated on the client-side, it is okay to submit the form. And, since we covered validation in the previous article, we're ready to submit! This article looks at what happens when a user submits a form — where does the data go, and how do we handle it when it gets there? We also look at some of the security concerns associated with sending form data.

## Client/server architecture

At it's most basic, the web uses a client/server architecture that can be summarized as follows. a client (usually a web browser) sends a request to a server (most of the time a web server like Apache, Nginx, IIS, Tomcat, etc.), using the HTTP protocol. The server answers the request using the same protocol.

![forms](Images301/forms.png)

- An HTML form on a web page is nothing more than a convenient user-friendly way to configure an HTTP request to send data to a server. This enables the user to provide information to be delivered in the HTTP request.

- The names and values of the non-file form controls are sent to the server as name=value pairs joined with ampersands. The action value should be a file on the server that can handle the incoming data, including ensuring server-side validation. The server then responds, generally handling the data and loading the URL defined by the action attribute, causing a new page load (or a refresh of the existing page, if the action points to the same page).

How the data is sent depends on the method attribute.

## The method attribute

The method attribute defines how data is sent. The HTTP protocol provides several ways to perform a request; HTML form data can be transmitted via a number of different methods, the most common being the GET method and the POST method

To understand the difference between those two methods, let's step back and examine how HTTP works. Each time you want to reach a resource on the Web, the browser sends a request to a URL. An HTTP request consists of two parts: a header that contains a set of global metadata about the browser's capabilities, and a body that can contain information necessary for the server to process the specific request.

## The GET method

- The GET method is the method used by the browser to ask the server to send back a given resource: "Hey server, I want to get this resource." In this case, the browser sends an empty body. Because the body is empty, if a form is sent using this method the data sent to the server is appended to the URL.

Consider the following form:

        <form action="http://www.foo.com" method="GET">
        <div>
            <label for="say">What greeting do you want to say?</label>
            <input name="say" id="say" value="Hi">
        </div>
        <div>
            <label for="to">Who do you want to say it to?</label>
            <input name="to" id="to" value="Mom">
        </div>
        <div>
            <button>Send my greetings</button>
        </div>
        </form>

- Since the GET method has been used, you'll see the URL www.foo.com/?say=Hi&to=Mom appear in the browser address bar when you submit the form.

## The POST method

The POST method is a little different. It's the method the browser uses to talk to the server when asking for a response that takes into account the data provided in the body of the HTTP request: "Hey server, take a look at this data and send me back an appropriate result." If a form is sent using this method, the data is appended to the body of the HTTP request.

Let's look at an example — this is the same form we looked at in the GET section above, but with the method attribute set to POST.

        <form action="http://www.foo.com" method="POST">
          <div>
            <label for="say">What greeting do you want to say?</label>
            <input name="say" id="say" value="Hi">
          </div>
          <div>
            <label for="to">Who do you want to say it to?</label>
            <input name="to" id="to" value="Mom">
          </div>
          <div>
            <button>Send my greetings</button>
          </div>
        </form>

When the form is submitted using the POST method, you get no data appended to the URL, and the HTTP request looks like so, with the data included in the request body instead:

        POST / HTTP/2.0
        Host: foo.com
        Content-Type: application/x-www-form-urlencoded
        Content-Length: 13
        
        say=Hi&to=Mom

### REFERENCE

- HTML5 Forms Reference [Check it out](https://htmlreference.io/forms/)

- Video Series on Styling HTML5 Forms [Check it out](https://www.youtube.com/playlist?list=PL4cUxeGkcC9g5_p_BVUGWykHfqx6bb7qK)

- Sending form data [Read the full article here](https://developer.mozilla.org/en-US/docs/Learn/Forms/Sending_and_retrieving_form_data)

## [Main page](https://amjadmesmar.github.io/reading-notes/)