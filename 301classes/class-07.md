# How I explained REST to my brother

SuperAgent

SuperAgent is light-weight progressive ajax API crafted for flexibility, readability, and a low learning curve after being frustrated with many of the existing request APIs. It also works with Node.js!

        request
    .post('/api/pet')
    .send({ name: 'Manny', species: 'cat' })
    .set('X-API-Key', 'foobar')
    .set('Accept', 'application/json')
    .then(res => {
      alert('yay got ' + JSON.stringify(res.body));
     });

## Request basics

- A request can be initiated by invoking the appropriate method on the request object, then calling .then() (or .end() or await) to send the request. For example a simple GET request:

        request
        .get('/search')
         .then(res => {
          // res.body, res.headers, res.status
          })
         .catch(err => {
           // err.message, err.response
          });

- HTTP method may also be passed as a string:

        request('GET', '/search').then(success, failure);

- Old-style callbacks are also supported, but not recommended. Instead of .then() you can call .end():

        request('GET', '/search').end(function(err, res){
        if (res.ok) {}
        });

- Absolute URLs can be used. In web browsers absolute URLs work only if the server implements CORS.

         request
        .get('https://example.com/search')
        .then(res => {

        });

## GET requests

- The .query() method accepts objects, which when used with the GET method will form a query-string. The following will produce the path /search?query=Manny&range=1..5&order=desc.

        request
         .get('/search')
         .query({ query: 'Manny' })
         .query({ range: '1..5' })
         .query({ order: 'desc' })
         .then(res => {

          });

- Or as a single object:

        request
         .get('/search')
        .query({ query: 'Manny', range: '1..5', order: 'desc' })
        .then(res => {

          });

- The .query() method accepts strings as well:

          request
           .get('/querystring')
          .query('search=Manny&range=1..5')
          .then(res => {

           });

- Or joined:

        request
                 .get('/querystring')
                 .query('search=Manny')
                 .query('range=1..5')
                       .then(res => {

                   });




**References:**

- How I explained REST to my brother [Read the full article here](https://visionmedia.github.io/superagent/)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
