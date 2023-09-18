- Question 1: [useRef](#1-script-vs-script-async-vs-script-defer)
- Question 2: [prototypal inheritance](#2-explain-prototypal-inheritance)
- Question 3: [this](#3-explain-this-in-javascript)
- Question 4: [let vs var vs const](#4-let-vs-var-vs-const)
- Question 5: [arrow functions vs regular functions](#5-arrow-functions-vs-regular-functions)
- Question 6: [hoisting](#6-what-is-hoisting)
- Question 7: [== vs ===](#7-==-vs-===)
- Question 8: [null vs undefined vs undeclared](#8-null-vs-undefined-vs-undeclared)
- Question 9: [.call vs .apply](#9-call-vs-apply)
- Question 10: [localstorage vs sessionstorage vs cookies](#10-localstorage-vs-sessionstorage-vs-cookies)
- Question 11: [event bubbling](#11-event-bubbling)
- Question 12: [event delegation](#12-event-delegation)
- Question 13: [what is a callback](#13-what-is-a-callback)
- Question 14: [what are promises](#14-what-are-promises)
- Question 15: [synchronous vs asynchronous functions](#15-synchronous-vs-asynchronous-functions)
- Question 16: [async/await vs promises](#16-async/await-vs-promises)

## All Questions

### 1. script vs script async vs script defer

<details>
<summary>Answer</summary>

- async scripts fetched in order in order but execute as soon as possible and do not block the HTML parser (no render blocking), so in a sense you cannot guarantee the order of execution

- defer scripts are fetch in order as well but execute only after HTML parsing is complete, so they are executed in order (great for scripts that rely on each other)

- when you have async and defer in the same script, async takes precedence, unless browser does not support async

</details>

### 2. Explain prototypal inheritance

<details>
<summary>Answer</summary>

- all javascript objects have a `__proto__` property that is a reference to another object, which is called the object’s prototype. (except objects created with `Object.create(null)`)
- when a property is accessed on an object and the property is not found, it will look at the parent’s proto and the parent’s proto’s proto until it is found
- similar to inheritance
</details>

### 3. Explain this in javascript

<details>
<summary>Answer</summary>

- basically the context of the function
- it depends on how the function is called (there are many rules that affects the context of `this`)
- `new` used to call function: `this` is the newly created object
- `call`, `apply`, `bind` used to call function: `this` is the object passed in as the first argument

further reading: https://medium.com/codeburst/the-simple-rules-to-this-in-javascript-35d97f31bde3

</details>

### 4. let vs var vs const

<details>
<summary>Answer</summary>

|             | var            | let         | const       |
| ----------- | -------------- | ----------- | ----------- |
| Scope       | function scope | block scope | block scope |
| Reassigning | yes            | yes         | no          |
| Redeclaring | yes            | no          | no          |
| hoisting    | yes            | no          | no          |

</details>

### 5. arrow functions vs regular functions

<details>
<summary>Answer</summary>

- simplified syntax
- `this` in arrow functions are lexically scoped (references parent's context)
- `this` in regular functions are locally scoped (references the function's context)
- there is no `arguments` object in arrow functions

</details>

### 6. what is hoisting

<details>
<summary>Answer</summary>

- being able to be referenced in code before they are declared
- only declarations are hoisted, assignments are left in place

- JS’s default behaviour of moving variables and functions to the top of their scope before code execution (only moves declaration, assignment left in place)
- function declaration vs function expression

  - function declaration has body hoisted but expression only has variable declaration hoisted

  ```jsx
  // Function Declaration
  console.log(foo); // [Function: foo]
  foo(); // 'FOOOOO'
  function foo() {
    console.log("FOOOOO");
  }
  console.log(foo); // [Function: foo]
  // Function Expression
  console.log(bar); // undefined
  bar(); // Uncaught TypeError: bar is not a function
  var bar = function () {
    console.log("BARRRR");
  };
  console.log(bar); // [Function: bar]
  ```

- reference error (let and const, because the variables are not declared/initialised, acts more of a temporary dead zone) vs undefined (var)

</details>

### 7. == vs ===

<details>
<summary>Answer</summary>

- `==` checks for equality of value, but not type
- `===` checks for equality of value and type
- in general do not use `==` because it can lead to funky results (1 ==[1] is true) except for convenience when comparing `null` and `undefined` (null == undefined is true)

</details>

### 8. null vs undefined vs undeclared

<details>

<summary>Answer</summary>

- `null` is a value that has been explicitly assigned the `null` value
- `undefined` is a value that has been declared but not assigned a value
- `undeclared` variables are created when you assign a vlaue to an identifier that has no previously been declared

- good habit to never leave variables `undeclared`. Explicitly assign null after declaring if you don't intend to use them yet
</details>

### 9. .call vs .apply

<details>
<summary>Answer</summary>

- both `.call` and `.apply` are used to call a function with the first parameter as the value of `this` and arguments provided individually (comma-separated) or as an array respectively

</details>

### 10. localstorage vs sessionstorage vs cookies

<details>
<summary>Answer</summary>

## Similarities

Cookies, `localStorage`, and `sessionStorage`, are all:

- Storage mechanisms on the client side. This means the clients can read and modify the values.
- Key-value based storage.
- They are only able to store values as strings. Objects will have to be serialized into a string (`JSON.stringify()`) in order to be stored.

## Differences

| Property                               | Cookie                                                   | `localStorage` | `sessionStorage` |
| -------------------------------------- | -------------------------------------------------------- | -------------- | ---------------- |
| Initiator                              | Client or server. Server can use `Set-Cookie` header     | Client         | Client           |
| Expiry                                 | Manually set                                             | Forever        | On tab close     |
| Persistent across browser sessions     | Depends on whether expiration is set                     | Yes            | No               |
| Sent to server with every HTTP request | Cookies are automatically being sent via `Cookie` header | No             | No               |
| Capacity (per domain)                  | 4kb                                                      | 5MB            | 5MB              |
| Access                                 | Any window                                               | Any window     | Same tab         |

</details>

### 11. event bubbling

<details>
<summary>Answer</summary>

- propagation of events in the DOM
- an element will attempt to handle and en event if there is a listener attached, then the event bubbles up to its parent and does the same time, all the way up to `document`
- can prevent bubbling by calling `event.stopPropagation()`
</details>

### 12. event delegation

### 13. what is a callback

### 14. what are promises

<details>
<summary>Answer</summary>

- promises are objects in javascript that represents the eventual completion of an asynchronous operation
- a promise has 3 states, fulfilled, rejected and pending
- either resolved or rejected
- promises are a way to handle async operations in javascript. they are js object that represents the eventual completion of the async operation. If the async operation succeeds, the promise is said to be resolved, else it is rejected.

Further readings: https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Promises

</details>

### 15. synchronous vs asynchronous functions

<details>
<summary>Answer</summary>

- Synchronous functions are blocking while asynchronous functions are not. In synchronous functions, statements complete before the next statement is run. In this case, the program is evaluated exactly in order of the statements and execution of the program is paused if one of the statements take a very long time.

- Asynchronous functions usually accept a callback as a parameter and execution continue on the next line immediately after the asynchronous function is invoked. The callback is only invoked when the asynchronous operation is complete and the call stack is empty. Heavy duty operations such as loading data from a web server or querying a database should be done asynchronously so that the main thread can continue executing other operations instead of blocking until that long operation to complete (in the case of browsers, the UI will freeze).
</details>

### 16. async/await vs promises

<details>
<summary>Answer</summary>

- we use async/await to avoid callback hell (lots of `.then` chaining is hard to read, also makes error handling hard as we need to handle errors in each `.then` block)
- async/await is syntactic sugar for promises
