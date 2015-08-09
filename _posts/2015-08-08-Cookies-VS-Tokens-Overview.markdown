---
layout: post
title:  "Cookies vs. Tokens for SPAs"
date:   2015-08-08 19:40
categories: mediator feature
tags: featured
image: /assets/article_images/2014-11-30-mediator_features/night-track.JPG
---

Cookie based authentication has been around for a long time. Basically, your browser stores a session ID that is generated and stored on the server. The server holds the users' session information. But when building a single page application (SPA), the client doesn't know who the user is or what they're authorized to access.

Token based auth is a newer approach, in which the signed token is sent to the server on each request and validated before the server sends a response. JSON Web Tokens (JWTs) are submitted with the requests either as an authentication header or in a query string. If you've ever looked at the outbound HTTP headers when using a service that uses tokens, you'll see an `Authorization:` header with `Bearer` and the JWT along with it, which is encoded in Base64.

Tokens are much better suited for SPAs because the token itself can contain information about access control - when navigating to a certain route, what should the user see if they are logged in vs. logged out? Since the state is stored on the client now, it can handle these types of things.