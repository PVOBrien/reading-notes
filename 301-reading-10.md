## The Call Stack

### [The Call Stack defined on MDN](https://developer.mozilla.org/en-US/docs/Glossary/Call_stack)
### [Understanding the JavaScript Call Stack](https://www.freecodecamp.org/news/understanding-the-javascript-call-stack-861e41ae61d4)
### [JavaScript Error Messages](https://codeburst.io/javascript-error-messages-debugging-d23f84f0ae7c)

The call stack: Last In, First Out, or LIFO. It's a way of understanding or organizing how the order of operations is for your code, for what happens in a function, that in a function, in order to resolve a given function, it has to resolve all code within it. Meaning, if that function has a function within it that function must be resolved prior to completing the first function, and on and on, much like nested for loops, that whatever is "farthest in" must be completed and returned before the previous one can resolve.

In [Understanding the JavaScript Call Stack](https://www.freecodecamp.org/news/understanding-the-javascript-call-stack-861e41ae61d4), it does reference the wellknown "stack overflow" error, and I'm not so confident to paraphrase, so here is the quote in it's entirety:

> What causes a stack overflow?
> A stack overflow occurs when there is a recursive function (a function that calls itself) without an exit point. The browser (hosting environment) has a maximum stack call that  > it can accomodate before throwing a stack error.

The best I can think of it, is it's a cyclical argument, that it calls itself as it's own argument, and hence round and round it will go ever and on.

[JavaScript Error Messages](https://codeburst.io/javascript-error-messages-debugging-d23f84f0ae7c) is a whole tutorial, that walks through common and helpful means of testing JavaScript, starting with the console, moving onto try catch code blocks, and then ending up with VS code extensions that can help (linter being one) and I will eventually check out [quokka](https://quokkajs.com/), as it looks like it is built to catch errors, but before i turn that on, I really want to be able to know more of what errors come up "natively" in JavaScript before I start using something to get me there faster. I want to be able to walk well before running.
