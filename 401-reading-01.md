# [Java Basics](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/index.html)

## Variables

First that stands out is a definition of "static" vs non-static variables. The way I read it, if it is "static" it basically means that it's a shared variable for a whole class, ie if you were to make a class for cars, then a likely __static__ variable would be the car's make and model, such that all Toyota (make) Priuses (model) will all (and likely always) be those two things. But, each car is very likely to have non-static variables such as speed, mileage, trim - variables that change from one Toyota Prius to another. Additionally, the __final__ keyword turns such variable into the Javascript equivalent of __const__.
Secondly, variable naming convention is camelCase.

### Primitive Data Types

Instead of var/let/const in JavaScript, instead you initialize(?) a variable by declaring its type. Straightforward enough, although I'm not yet understanding why for float or double that even after declaring them you have to end them with f or d respectively. Seems redundant, it does.
Also I'm assuming that there are numerous options for integers is for memory allocation, so as to not take up significantly more space for a value than is needed (within reason, whatever reason that is, probably some standard bit/byte allocation block size, or something? idk, it's a guess).

It also makes mention that you don't have to use the __new__ keyword for primitives, as they are literals. Which, thank goodness I guess, because otherwise the __new__ keyword would be littered everywhere. O.o

For integers you can use an underscore _ to seperate numbers in a numerical literal.

## Arrays

Arrays are of course powerful and useful, but I am currently apprehensive that you have to declare how many items/index positions will be within the array at the time of the array's creation. That seems to me to limit the arrays usefulness, or that you have to add additional (creative) steps ahead of time to ensure that an array will be able to contain what might/should/need to be a dynamic number of index positions for an unknown number of array items. But wait... a multidimensional array [][] doesn't need to declare its index positions? :headscratch: #tobecontinued, no doubt.

Also, arrays are not literals, they must be initialized with the __new__ keyword.






A word about "information hiding": why does it matter? Is this just semantics, or is there some "code security" idea that I'm missing here, where "seeing" some code could be "dangerous", or is it more about streamlining what code can be utilized by a given object, and pruning out the stuff that doesn't matter for that object so as to ensure that code only does what it should?


# [What Does it Mean to Compile Code?](https://www.reddit.com/r/explainlikeimfive/comments/233dq5/eli5_what_does_it_mean_to_compile_code/)

Compiling = turning human-readable content into machine-readable content. As opposed to interpreted code/languages that reads the code as-is and executes that. Not that it _doesn't_ turn the code into machine-readable as that _has_ to happen, but that there isn't any such executable of machine-readable-only code ever.

On the whole, it's safe to say that languages that require compiling are "lower" languages, or another term I've heard is "closer to the metal", where the closer it is to just ones and zeros, the lower the language is.

# Compiling (as described by XKCD)

![Compiling_XKCD](https://imgs.xkcd.com/comics/compiling.png)

Compiling takes time. This sounds very similar to when I'm rendering a video, and it has to put together: graphics, render audio and audio effects, video and audio fades, change the video format, audio formats... and that's if I went and pre-rendered other parts of the vidoe so it wouldn't have to go and do that. In Java, it has to find all the classes, libraries/dependencies (and those should all be the _correct_ libraries/dependencies), and other pieces of the program that I'm as-of-yet unaware of.

# [Reading Java Documentation](https://www.dummies.com/programming/java/making-sense-of-javas-api-documentation/)

Java seems much more involved than JavaScript. Thanks goes out to the "dummies" who made a quick sheet how to best skim/peruse the Java documentation. And then it's whole 'other thing to get that documentation working in the project. But, first steps here.
