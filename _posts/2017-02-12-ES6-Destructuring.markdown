---
layout: post
title:  "ES6 Destructuring"
date:   2017-02-12 12:50
categories:
tags: javascript es6 es2015
---

### What is destructuring?
ES6 (more formally known as ES2015) brings a lot of helpful language features
to Javascript. Arrow functions that make writing method functions easier, block scoping via `let`, and native support for Promises are some of the features I am most excited about.

Another interesting feature is _destructuring_, which allows us to extract values
from objects and arrays with a more concise syntax.

---

### Array destructuring
The syntax (technically, it is called a `pattern`) for destructuring arrays looks like an array itself:
{% highlight javascript %}
const [x] = [1, 2, 3]
console.log(x) // 1
{% endhighlight %}

The position of `x` is important. If you want to ignore the first element, and only choose the second element, you can add leading comma's:
{% highlight javascript %}
const [, x] = [1, 2, 3]
console.log(x) // 2
{% endhighlight %}

Another example of array destructuring:

{% highlight javascript %}
const foods = ['Pizza', 'Hamburgers', 'Salad', 'Ice Cream'];
const [x, y] = foods;
console.log(`I like ${x} and ${y}`);
// Output: I like Pizza and Hamburgers
{% endhighlight %}

`x` and `y` are assigned to the first and second values in the `foods` array. The destructuring syntax, `[x, y]`, remains on the left side of the assignment, as we are declaring those variables. The right side is the data to destructure.

Combined with the `spread` operator, we can also extract certain values while assigning the remaining elements to a variable:

{% highlight javascript %}
const [favorite, ...rest] = foods;
console.log(favorite); // 'Pizza'
console.log(rest); // ['Hamburgers', 'Salad', 'Ice Cream']
{% endhighlight %}


### Object destructuring
Extracting values from arrays is cool, but I think the real bread and butter of destructuring is objects.

{% highlight javascript %}
const { x } = { x: 1, y: 2 };
console.log(x) // 1
{% endhighlight %}

Similar to array destructuring, the syntax _represents the structure we wish to extract data from._ Instead of the position of `x` being important, it is the name of the key to extract.

{% highlight javascript %}
const { age } = { name: 'Kam Harrah', age: 24 };
console.log(age) // 24
{% endhighlight %}

Multiple values can be extracted by separating the variables by commas:
{% highlight javascript %}
const { name, age } = { name: 'Kam Harrah', age: 24 };
console.log(name) // "Kam Harrah"
console.log(age) // 24
{% endhighlight %}

Sometimes, you may want to extract from a certain key, but name the variable something else.

{% highlight javascript %}
// { keyName: variableName }
const { age: userAge } = { name: 'Kam Harrah', age: 24 };
console.log(userAge) // 24
{% endhighlight %}

We can also use `defaults` when extracting data that may not exist:

{% highlight javascript %}
const { name, favoriteColor = 'Green'} = { name: 'Kam Harrah', age: 24 };
console.log(favoriteColor); // 'Green'
{% endhighlight %}

We can extend object destructuring to parameters of a function.

{% highlight javascript %}
// Instead of:
function handler(response) {
    if (response.err) {
        throw Error(err);
    }

    response.data = response.data || {};

    doSomethingWith(response.data);
}

// You can do:
function handler({err, data = {}}) {
    if (err) {
        throw Error(err);
    }

    doSomethingWith(data);
}
{% endhighlight %}

### Conclusion

Destructuring provides a shortcut to do something very common - extract data.
Combined with other ES6 language features, our JS code becomes much more concise and readable. There's many other use cases for destructuring to explore!

I recommend going through the destructuring section of [ES6 Katas](http://es6katas.org/) or reading through [Exploring ES6](http://exploringjs.com/es6/ch_destructuring.html) for more advanced use cases.