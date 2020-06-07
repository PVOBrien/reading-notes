# JS Object Literals; The DOM, and *Understanding the Problem Domain*

## Literals

I read the assigned pages, and there is just so much content to digest and I am having difficulty comprehending the concepts without tangible examples and on-hand code. Nevertheless, here are my take aways and notes below.

What is an object? (pp 100-101)
- Objects are variables that can contain further variables and functions.
- Within objects, variables are called properties (usually in a name:value pairing) and functions are called methods. However both properties and methods within objects are syntactically alike to variables and methods. Only the name is different.

Creating an Object:Literal Notation (102)
- To create an object, you declare a variable (var *name*)
  - define your properties (with name:value pairs) and end the line with a comma (,)
  - define your methods. Starting out the same as properties (like a name:value pair) wherein:
    - the name of the name:value pair is the method name, followed by a colon (:) then you declare it as a function() {
    - write the code
    - close it with a closed curly bracket
  - close the whole object in a closed curly bracket

Accessing an Object, and Dot Notation (p 103)

In Javascript, accessing properties and methods is accomplished using dot notation, wherein you call the object immediately followed - no space - by a dot (.) immediately followed by the property or method being referenced. This can then be referenced in a variable for easier recall.

__NOTE__: you can use either square brackets instead of dots to call an object and property/method name.

## The DOM - Document Object Model

The Document Object Model (DOM) is "how Javascript can access and update the contents of a webpage" (p. 184). It's also basically the same as an Application Programming Interface (API), as the capability for online services to be called and referenced as specific objects and their properties and methods in other applications.

The DOM Tree is a web page represented as a tree with trunks and branches representing the elements and attributes (and properties?) of html and css so as to allow JS to reference/access and modify the webpage (via html elements).  
- JavaScript (JS) accesses the DOM tree by selecting either an html attribute, a css attribute, or a combination of both. The following selection of commands are used common ways to select webpage elements
  - Individual Element Node Selection
    - getElementById() accesses an element by their defined html ID
    - querySelector() accesses the _first matching element_ as defined by the css selector
  - Multiple Element Selection (Nodelist_
    - getElementsByClassName() accesses all element that have that specific css class attribute
    - getElementsByTagName() selects all elements that have the specified tag name
    - querySelectorAll() uses a css selector to choose all matching elements
  -Element Node Traversal methods
    - parentNode selects the parent of the current element node
    - previousSibling / nextSibling selects the previous or next simbling from the DOM tree
    - firstChild / lastChild - selects the first or last child of the current element
- After accessing an element or element node, you can make calls to modify what is accesses (this is accomplished with nodeValue) which can then be modified by:
  - innerHTML
  - textContent
  - createElement()
  - createTextNode()
  - appendChild() / removeChild()
- You can check if that node has elements within it by using:
 - hasAttribute()
 - getAttribute()
 - setAttribute()
 - removeAttribute()

It will ultimately looks something like this (as on page 194):
> document.getElementById('parameterName')

Elements can be selected from a node by using either the item() method or an array syntax

item() method 

>        var elements = document.getElementsByClassName('hot")
>          if (elements.length >= 1( {
>          var firstItem = elements.item(0);
>        }

Array Syntax

>        var elements = document.getElementsByClassName('hot")
>          if (elements.length >= 1( {
>          var firstItem = elements.item[0];
>        }

## Updating Text Content via innerHTML or textContent

These two methods have advantages and concerns. Updating content by way of innerHTML is a danger due to exposing the website to running third party / user-inputted code that could be malicious. But it is faster overall. textContent (by way of DOM manipulation) is slower but safer. So what method you choose is heavily dependent on the task at hand.

## Accessing and modifying HTML via DOM manipulation

Much of the 40 pages of reading on the matter of Document Object Model is dedicated to understanding showing how to reference, access, and modify the html and what is onscreen. However, until I see this in action, it is too theoretical for me to do anything beside parrot what is in our text books.

**NOTE**: Due to the volume of content in this reading assignment, and how I cannot currently envision how this works, I have not yet updated my flashcards. I hope to do so upon understanding the content and having the time to do so.

# Understanding The Problem Domain Is The Hardest Part Of Programming

Making mention of waterfall and agile style methods, author John Sonmez discusses the importance of understanding the problem, and therefore being able to deduce the correct solution, and plot a course of action accordingly. Because without understanding what needs to be completed (alongside any other requirements) it is likely your solution isn't the correct one (or could be more correct).

So: Know what you're working on, the problem and the scope, before coding.

> ‘Would you tell me, please, which way I ought to go from here?’
> 
> ‘That depends a good deal on where you want to get to,’ said the Cat.
> 
> ‘I don’t much care where—’ said Alice.
> 
> ‘Then it doesn’t matter which way you go,’ said the Cat.
> 
> ‘—so long as I get somewhere,’ Alice added as an explanation.
> 
> ‘Oh, you’re sure to do that,’ said the Cat, ‘if you only walk long enough.’
>
> ***Lewis Carrol, Alice’s Adventures in Wonderland***
