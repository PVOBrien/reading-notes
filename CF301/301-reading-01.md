# SMACSS and Responsive Web Design

## [Responsive v Adaptive v Mobile](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/)
  Each of these are unique, albeit similar. Mobile is the farther from the other two, as it requires additional code, and the ability to know what browser to render for, more specifically than if it were just any browser, but a _mobile_ browser. Hence, building a responsive and/or adaptive website makes more sense.
  vw, vh, vmin, and vmax are all css attributes that work to enable responsive and adaptive browsers.

  > target / context = result

is the formula to make it happen. That and float:right; and float:left; bu the looks of it.
  
To a certain point. After that: media queries. Most commonly...

  > @media all and (min-width: 320px) and (max-width: 780px) {...}

which allows for building websites to account for both mobile and desktop

There's also accomodations for (orientation: landscape) when the width/height change (such when a phone is rotated), as is a (min-resolution: ###dpi), which I'm not quite certain why that's important, and the article doesn't explain it's usefulness, but it is available.

### Mobile First

With so many different screensizes, today it is prudent to aim for the devices it will most likely be viewed on: a smartphone. This way, it can be more focused on the needs of the device with potentiallly (likely) the least necessary data-intensive assets, and look correct on the most viewed screen. There are additional media queries at play here, which will need to be broken down further for me to understand.
    <meta name="viewport" content="width=device-width">
That above snippet is another method with which to aright a webpage's content.
    <meta name="viewport" content="user-scalable=yes">
And that above code allows for proper scalling for accessibility purposes.

There is _much more_ about this I'm not able understanding at the moment, but this article lays out the groundwork for future discussion.

------------------
## [All About Floats](https://css-tricks.com/all-about-floats/)

Float - right or left, it puts that content to that far direction.
Clear - right or left, both, or none,  it ensure that nothing is floated _on that side of it_.

Using floats comes with challenges.It can make elements behave counterintuitively, and in some cases, just simply "very utilitarian", and you need to stop it. The following html line puts a clear break into the page, and causes the float's to "restart" in a way. It is not the prettiest bit of code is the opinion (so says the article) but it does do the trick.
> <div style="clear: both;"></div>
The Overflow Method -  is mentioned, to put Overflow: auto _OR_ hidden; but, seems to have basically the same issues as the Empty Div Method.
So there's the Easy Clearing Method:
```
  .clearfix:after { 
    content: "."; 
    visibility: hidden;
    display: block;
    height: 0;
    clear: both;
  }
```
which seems to just add a little coding content at the end of the element, and clearing the float this way.

It would seem they all accomoplish the same goal; use whichever fits the need of your code best.

A Final Note: Nobody likes Internet Explorer. And nobody uses it anymore (finally and good riddance is the concensus).

---------------
## [Don't Overthink It Grids](https://css-tricks.com/dont-overthink-it-grids/)

Grids: prior to css grid or flexbox, this is how it was done. Using css classes to apportion via percentages to achieve simple, linear grids. It's necessary to clear content to get it to look correctly, and you need to use box-sizing: border-box; (and include for -webkit and -moz) to keep the gutters from making the format behave peculiar, but this will get you a long way.
NOTE: At the end Sass and SCSS/Compass is mentioned. This is my first contact with it.

## [CSS Floats Explained By Riding An Escalator](https://www.freecodecamp.org/news/css-floats-explained-by-riding-an-escalator-57fa55232333/)

I'll need to have this close by when i use floats again, and see the analogy of how courteous usage of escalator aligns with how floats behav.

## [Scalable and Modular Architeture for CSS](http://smacss.com/)

__It's a whole book on how to use CSS to organize webpages.__ 
