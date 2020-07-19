## EJS, or Embedded JavaScript, or quicker coding, closer.

EJS = Embedded JavaScript. JS, right in the browser. Using <% %> you can write code directly into your html files, and with <%= CODEBLOCK %> it can evaluate content. I'm still uncertain in this use case how writing Javascript that will be read within the htiml is different from the ability to evaluate code within an EJS block. There is also whole sale webpage templating available, although for me the tutorial didn't really show an intriguing or particularly helpful example, but once I see a full walkthrough, it'll be like a one-step-less and more immediate version of mustache. 

If EJS is going to be used a couple new lines of code are introduced to make the library available and associate it. 

---- 

> var bodyParser = require('body-parser'); 

> var expressLayouts = require('express-ejs-layouts'); 

> app.use(bodyParser()); 

> app.use(expressLayouts); 

---- 

and with those lines of code, your html page can now have Javascript coded within it, and use html tags outside of the <% %> as the indicators for "for" loops, and I'm certain other coding and templating purposes. For the whole of it, EJS has their website with [documentation available](https://ejs.co/), and to better understand it, I will be going back through the suggested tutorial that has both an [instructions/follow-along guide](https://scotch.io/tutorials/use-ejs-to-template-your-node-application) and a [github repo for the code](https://github.com/scotch-io/node-ejs).
