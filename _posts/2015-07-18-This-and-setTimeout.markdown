---
layout: post
title:  "This and setTimeout"
date:   2015-07-18 14:34:25
categories: hackreactor feature javascript
tags: hackreactor javascript
image: /assets/article_images/2015-07-18-this-and-settimeout/memento.jpg
---

There is a common problem all JS developers run into at some point.

The `this` binding is tricky to use. The power (and confusion) of `this` stems from the fact that it can be bound to different things depending on how the function or method is called. In some instances, though, it seems like the code [completely forgets](http://www.imdb.com/title/tt0209144/) what the `this` binding refers to.

Most of the time, you can assume that it will be bound to whatever is to the left of the calltime dot (the dot right before the method call)
    
    var obj = {
      met: function() {
        console.log(this);
      }
    }
    obj.met() // logs the object

Following this logic, it would make sense that the binding would stay the same when using setTimeout() or setInterval().
    
    setTimeout(obj.met, 1000);
    // Logs ???

However, because of what's going on under the hood, `this` will refer to the global `window` object in the browser, NOT the object.

# Under the hood

The reason this happens is because setTimeout executes the callback function you give it (in our case, `obj.met`) inside of a different *execution context*. An excellent description of what an execution context [can be found here](http://davidshariff.com/blog/what-is-the-execution-context-in-javascript/). In short, it basically means the scope the function is being evaluated in _at runtime_ is much different than the what the scope looks like in code. Our expectation that the in-memory models of our code will be laid out like the code on our screen is flawed, and thinking in terms of execution contexts can help when running into problems like this.

# The solution(s) to this problem

There are a few ways to successfully refer to `this` in the right context when using these functions.

One way is to wrap the method call inside of an anonymous function:
  
    setTimeout(function() {
      obj.met(); // make sure to call the method with ()
    }, 1000)

    // Logs `obj` correctly

Another way is to `bind` the object that we want `this` to refer to, to the method inside of setTimeout:

    setTimeout(
      obj.met.bind(obj);
    , 1000)

Interestingly enough, these two examples do exactly the same time. All `bind` does is wrap the function it is called on inside of an anonymous function. Personally, I like to use bind, as I think it makes the code a lot cleaner. However, you should use whichever way you like best.

