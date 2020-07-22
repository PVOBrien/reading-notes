## Sending Form Data (Update & Delete)

[Here](https://developer.mozilla.org/en-US/docs/Learn/Forms/Sending_and_retrieving_form_data) is where some burning questions of mine are answered. What is the

> "action="

attribute actually doing? It's telling the click where it is going. Sure, it did do that, but it still felt nebulous, as if it were more "retrieving" that place, not really "going" to it. The idea is still weird, but just reading that in documentation helps solidify the idea of what's going on. Also, the absolute (https://example.com) vs relative (/anotherurl) was a helpful comparison, I was thankful to see the two examples so close to each other.

Moving to the GET method: in an input tag, the name is the key and value is... well it's the value! And it shows up in the URL when you send it, (simply, before security measures run prior/when it hits middleware to hide sensitive data)! Further down in "Viewing HTTP requests" it makes mention to never send sensitive data via GET, because it comes across in plain characters.

POST is more complicated, and I'm uncertain how to parse what all's going on there right now, or how to use it all.

### Server Side details, retrieving the data
It gets into weeds I'm not sure about here. Our example work available in my github repo is a better walk-through example for Javascript at least.

### Sending Files
__noted here to look at later for a deeper dive to look into the complexities of files__

### Security Issues

There are broad best practices so that malicious code can't so easily run on your servers. These being:

1. Escape potentially dangerous characters. (Lest little bobby tables comes knocking.)
2. Limit the incoming amount of data. Less data = less amount of code able to run.
3. Sandbox uploaded files. I think this is related to the prerequisite to sanitize data, to put it through a intermediary that "takes the teeth" out of any dangerous code that might otherwise have been run if it didn't get "laundered".

## [Forms in HTML5](https://htmlreference.io/forms/)
This above link is a descriptive sheet page of all things forms, and is bookmarked for later use.

## [Styling HTML5 Forms](https://www.youtube.com/playlist?list=PL4cUxeGkcC9g5_p_BVUGWykHfqx6bb7qK)
A long format video walking through the process of building HTML5 forms.
