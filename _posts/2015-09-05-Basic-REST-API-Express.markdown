---
layout: post
title:  "A basic REST API in Express"
date:   2015-09-05 16:42
categories: 
tags: REST node express
image: /assets/article_images/2014-11-30-mediator_features/night-track.JPG
---

Express, a popular web application framework for Node.js, makes it very easy to set up basic routing for your server, which allows you to configure how your server responds to particular requests. One of the styles of defining these routes that your server responds to is called REST, and it's become one of the standard ways that server API's are implemented.

# Setting up Express
For this example, we'll be using Express 4.x.

Setting up Express is extremely easy. Use `npm install express` to add it to your project, and inside of your Node application file (we'll call ours `index.js`), add the following lines of code:

{% highlight javascript %}
var express = require('express');
var app = express();

app.get('/', function(req, res){
  res.send('Hello World!');
});

app.listen(1337, function () {
  console.log('Listening to port 1337!');
});
{% endhighlight %}

This is all it takes for a basic routing setup in express. `app.get('/')` handles any `GET` requests coming to the server, and calls the function you supply it. The two parameters passed into the callback are `req`, short for request, and `res`, short for response. We're using the `send` method on the response object to send back `'Hello World!'` to our client.

This is nice, but lets extend this to match our REST principles. Say we have a Product database, and we want to return product data. A good URL path that follows the REST format would be `/products/{id here}`, in which the client can append the ID of the product to the URL.

To handle this in Express is fairly simple

{% highlight javascript %}
app.get('/products/:id', function(req, res){
  var productId = req.params.id;
  // Retrieve information from database
  res.send(productData);
});
{% endhighlight %}

The `/products/` portion of our minimal router listens for any URLs that start with `/products/`, and `:id` lets Express know that we want to store that portion of the URL. This means that for `/products/12345`, `req.params.id` will be `12345`.

That's it for the basic example! To extend this functionality out further, check out the `Router` module of Express, which provides a way to modularize your routes.