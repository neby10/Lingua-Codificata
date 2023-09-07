# JavaScript Fundamentals

JavaScript classes are just objects. Here is an example..
~~~
class Dog {
  constructor(name) {
    this._name = name;
    this._behavior = 0;
  }

  get name() {
    return this._name;
  }
  get behavior() {
    return this._behavior;
  }   

  incrementBehavior() {
    this._behavior ++;
  }
}
~~~

**Static Methods**: A static method in JavaScript is a method that has a static keyword prepended to itself. Such methods cannot be accessed through instantiated objects but could be accessed through the class name. This is because static methods belong to the class directly.
~~~
static generatePassword() {
    return Math.floor(Math.random() * 10000)
}
~~~


**Callbacks** are a way to handle asynchronous code in JavaScript. They allow you to pass a function as an argument to another function, and the callback function will be executed when the first function finishes executing. Callbacks are often used to handle asynchronous operations, such as making HTTP requests or reading from a file.
~~~
function makeHttpsRequest(url, callback) {
  // Make an HTTP request.

  // Call the callback function when the request is finished.
  callback(response);
}

makeHttpsRequest('https://example.com/api/users', function(response) {
  // Handle the response.
});
~~~

**Promises** provide a more elegant and predictable way to handle asynchronous operations than callbacks. Promises represent the eventual completion or failure of an asynchronous operation. You can use promises to chain together asynchronous operations, and you can also use them to handle errors.

Promises are objects that represent the eventual outcome of an asynchronous operation. A Promise object can be in one of three states:
- Pending: The initial state— the operation has not completed yet.
- Fulfilled: The operation has completed successfully and the promise now has a resolved value. For example, a request’s promise might resolve with a JSON object as its value.
- Rejected: The operation has failed and the promise has a reason for the failure. This reason is usually an Error of some kind.

The Promise constructor method takes a function parameter called the executor function which runs automatically when the constructor is called. The executor function generally starts an asynchronous operation and dictates how the promise should be settled.

The executor function has two function parameters, usually referred to as the resolve() and reject() functions. The resolve() and reject() functions aren’t defined by the programmer. When the Promise constructor runs, JavaScript will pass its own resolve() and reject() functions into the executor function.

~~~
const executorFunction = (resolve, reject) => {
 if (someCondition) {
     resolve('I resolved!');
 } else {
     reject('I rejected!'); 
 }
}
const myFirstPromise = new Promise(executorFunction);
~~~

Promise objects come with an aptly named .then() method. It allows us to say, “I have a promise, when it settles, then here’s what I want to happen…”

.then() is a higher-order function— it takes two callback functions as arguments. We refer to these callbacks as handlers. When the promise settles, the appropriate handler will be invoked with that settled value.
- The first handler, sometimes called onFulfilled, is a success handler, and it should contain the logic for the promise resolving.
- The second handler, sometimes called onRejected, is a failure handler, and it should contain the logic for the promise rejecting.

One important feature of .then() is that it always returns a promise. We’ll return to this in more detail in a later exercise and explore why it’s so important.
~~~
let prom = new Promise((resolve, reject) => {
  let num = Math.random();
  if (num < .5 ){
    resolve('Yay!');
  } else {
    reject('Ohhh noooo!');
  }
});

const handleSuccess = (resolvedValue) => {
  console.log(resolvedValue);
};

const handleFailure = (rejectionReason) => {
  console.log(rejectionReason);
};

prom.then(handleSuccess, handleFailure);
~~~

Remember, .then() will return a promise with the same settled value as the promise it was called on if no appropriate handler was provided. This implementation allows us to separate our resolved logic from our rejected logic. Instead of passing both handlers into one .then(), we can chain a second .then() with a failure handler to a first .then() with a success handler and both cases will be handled.

~~~
prom
 .then((resolvedValue) => {
   console.log(resolvedValue);
 })
 .then(null, (rejectionReason) => {
   console.log(rejectionReason);
 });
~~~

Since JavaScript doesn’t mind whitespace, we follow a common convention of putting each part of this chain on a new line to make it easier to read. To create even more readable code, we can use a different promise function: .catch().

The .catch() function takes only one argument, onRejected. In the case of a rejected promise, this failure handler will be invoked with the reason for rejection. Using .catch() accomplishes the same thing as using a .then() with only a failure handler.

~~~
prom
 .then((resolvedValue) => {
   console.log(resolvedValue);
 })
 .catch((rejectionReason) => {
   console.log(rejectionReason);
 });

~~~

Mistakes
Mistake 1: Nesting promises instead of chaining them.
~~~
returnsFirstPromise()
.then((firstResolveVal) => {
  return returnsSecondValue(firstResolveVal)
    .then((secondResolveVal) => {
      console.log(secondResolveVal);
    })
})
~~~
Mistake 2: Forgetting to return a promise.
~~~
returnsFirstPromise()
.then((firstResolveVal) => {
  returnsSecondValue(firstResolveVal)
})
.then((someVal) => {
  console.log(someVal);
})

~~~

To maximize efficiency we should use concurrency, multiple asynchronous operations happening together. With promises, we can do this with the function **Promise.all()**.

Promise.all() accepts an array of promises as its argument and returns a single promise. That single promise will settle in one of two ways:
- If every promise in the argument array resolves, the single promise returned from Promise.all() will resolve with an array containing the resolve value from each promise in the argument array.
- If any promise from the argument array rejects, the single promise returned from Promise.all() will immediately reject with the reason that promise rejected. This behavior is sometimes referred to as failing fast.

~~~
let myPromises = Promise.all([returnsPromOne(), returnsPromTwo(), returnsPromThree()]);

myPromises
  .then((arrayOfValues) => {
    console.log(arrayOfValues);
  })
  .catch((rejectionReason) => {
    console.log(rejectionReason);
  });

~~~

~~~
function makeHttpsRequest(url) {
  return new Promise((resolve, reject) => {
    // Make an HTTP request.

    // If the request is successful, resolve the promise with the response.
    if (response.ok) {
      resolve(response);
    } else {
      // If the request fails, reject the promise with an error.
      reject(new Error('HTTP request failed.'));
    }
  });
}

const response = await makeHttpsRequest('https://example.com/api/users');
// Handle the response.
~~~

**Async/await** makes it easier to write asynchronous code by allowing you to write code that looks like synchronous code. Async/await allows you to write code that is more readable and maintainable than code that uses callbacks or promises directly.

~~~
async function makeHttpsRequest() {
  const response = await fetch('https://example.com/api/users');
  // Handle the response.
}

const response = await makeHttpsRequest();
// Handle the response.
~~~


**Closure**: A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). In other words, a closure gives you access to an outer function's scope from an inner function.