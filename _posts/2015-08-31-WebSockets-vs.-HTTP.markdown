---
layout: post
title:  "WebSockets vs. HTTP"
date:   2015-08-31 09:26
categories: javascript websockets http
tags: javascript
image: /assets/article_images/2014-11-30-mediator_features/night-track.JPG
---

I recently discussed the topic of WebSockets with someone, and they asked “Why hasn’t WebSockets gained more traction? It seems much more functional than AJAX!” That piqued my curiosity in the subject, so I decided to evaluate the pros and cons of these two methods of client / server communication.

##Brief Backstory
(skip over if you know how HTTP GET requests and AJAX work)

When we think of how the client / server model works, we usually think of a client requesting information from the server, and the server processing the request and sending back the necessary information (whether that’s HTML for a web page, data stored in a database, or a thumbs-up that something was created from a RESTful interaction). 

If this request uses TCP, it will involve a “handshake” process that sets up the connection between the client and server. Once the handshake has been made, the client sends the request to the server, and the server fulfills that request as soon as it can.

When you go to www.google.com, your browser is sending a request to the server that DNS resolves for you (one of many servers that will most likely send you a cached version of the site). Your browser will move from whatever page you were on to the newly fetched data, and you will see the Google site.

If you want to make a request without leaving your current page, such as grabbing a list of Amazon products (need better example) and displaying them within a small portion of your site, there is a technique called AJAX that will accomplish this. AJAX allows you to send requests in the background asynchronously, meaning that the page will not wait or hold all code execution until the request comes back - it will happen in the background, your page will continue to function, and once the request is received, the code you provide AJAX to handle the response will run.

##The Problem
In order to build any type of real-time application, this process is not efficient.

You could repeatedly send requests every X seconds to check for updates. This is called a traditional AJAX polling technique. But what if the server takes longer than X seconds to respond to one of the requests? Then, the data being returned could potentially be out of order. It could also be a huge waste of resources and bandwidth - the client and server have to `handshake` every time, and if nothing is changing or changing faster than your recurring requests, then it’s not as immediate as it could be. Wouldn’t it be better if the server could simply send the data as soon as it becomes readily available or when something changes?

##Long Polling
Long polling _was_ the way to accomplish this. With long polling, when the client requests something from the server, the server waits until it has the information available, and then sends the information. As soon as the client receives that information, it sends another request to the server, repeating the process.

But there's a better way.

Socket.IO is a Node library that utilizes WebSockets, and reverts to an older technique if WebSockets is not supported by the client’s browser. 

##WebSockets
WebSockets isn’t some fancy technique or snippet of code - it’s a protocol, and unlike HTTP, it is built to provide two-way communication over one TCP connection.
a persistent connection is made between the client and server. This eliminates the need for multiple handshakes (you only need one to establish the connection), and the server can send data back to the client whenever it needs to. Sockets are a little bit more cumbersome to set up, but are much easier to think about when bi-directional communication is necessary.

##Pros and Cons
AJAX is easy to implement when communication is solely one directional. Using a library like Socket.IO for simple requests would be overkill, not to mention harder to set up.

WebSockets are perfect for continuous bi-directional communication between the client and server. Implementing WebSockets takes a little more time, but is worth it. As for speed, [these guys recently performed a speed test](http://blog.innvenio.com/ajax-vs-socket-io-speed-battle/), and although Socket.io performed a little better, the differences were mostly negligable.

Happy coding!