# Spring

## [Spring App Basics](https://spring.io/guides/gs/serving-web-content)

After building the demo app, it was interesting that it "ran" at "75% executing". Also, there were a lot of dependencies/plugins to download to get it to run, I feel there's a lot going on under the hood to get it working. It uses the model-view-controller (MVC) model to organize, display, and gather data respectively, and it has it's own syntax for those responsibilities.

As for the application itself, it ran, there's a framework to impliment and use, and it's server. The internet is yours! 


## [Spring MVC and Thymeleaf](https://www.thymeleaf.org/doc/articles/springmvcaccessdata.html)

> In a typical Spring MVC application, @Controller classes are responsible for preparing a model map with data and selecting a view to be rendered.
A model map - in Spring, allows for complete abstraction of the view technoloby, and become a "Thymeleaf context object - which is, furthermore, _"part of the Thymeleaf template execution context"_

1. Spring model attributes

If its data that can be used for views, it is considered a model attribute, which in Thymeleaf is known as a context variable. Attributes can be created and/or manipulated with:

- .addAttribute
- ModeAndView potato = new ModelAndView(String message)
- @ModelAttribute(String message) - this is via Java Annotation

which adds the addribute to the model and is available in Thymeleaf views, acessible by syntac __${attributeName}__. Which, it notes, is a "Spring EL" aka Spring Expression Language expression that will allow for querying and "manipulating an object graph at runtime" (?).

2. Request parameters

Request parameters are standard enough; everything after the <query?> in the URL are the request parameters. The request parameters are multivalued, and index positions are available for them.

3. Session attributes: are available by using the session. prefix.

4. ServletContext attributes. "The ServletContext attributes are shared between requests and sessions." as stated in the article, available via  #servletContext. prefix.

5. Spring beans - Thymeleaf can access beans with the @beanName syntax.
