# Spring RESTful Routing & Static Files

## [Spring Request Mapping](https://www.baeldung.com/spring-requestmapping)

1. Overview - @RequestMapping annotation "is used to map web requests to Spring Controller methods".

2. @RequestMapping Basics

- by path, a "curl" method from the command line. (What is a curl?)
- HTTP Method = the _method_ parameter has no default. but it can be used to "Post some Foos"

3. RequestMapping and HTTP Headers

- with headers attibutes = to create more specific requests in the header, and you can have multiple headers this way.

- @RequestMapping "Consumes and Produces" - manages media types (and other types?) to be accepted and overrides the type-level information (?)

4. RequestMapping with Path Variables

- Single @PathVariable in order to return something specific with that @PathVariable.

- Multiple @PathVariable, available for more complex URIs (Uniform Resource Identifiers)

- @PathVariable with Regex. You can use regex to match.

5. RequestMapping with Request Parameters. It can be done, and the request parameters are used after extracting them from the URL.

6. RequestMapping Corner Cases - they exist if different methods reach the same Controller method

7. New Request Mapping Shortcuts (not that I knew the old one, but these seem to be much speedier ways of accomplishing their namesake methods)

- GetMapping
- PostMapping
- PutMapping
- DeleteMapping
- PatchMapping

8. Spring Configuration (is required to make it work. no surprises here.)

## [Accessing Data with JPA](https://spring.io/guides/gs/accessing-data-jpa) (Seems like this is Spring's database solution?)

Definition: __JPA__ : Java Persistence API. (They should really just "remind" people what that is the first time on any tutorial page. imo.)

- Create a Spring instance.
- Define a "Simple Entity". Reads like you'll be creating a POJO class, with the annotation of @Entity on top / in front of its public class modifiers (to note it is a JPA entity), as well as an @ID @GeneratedValue (wto ti the ID to the JPA). It can then store that JPA into a relational database (or does so automatically?).

It goes on to note that it uses an interface, that Spring JPA creates for the application "when you run the application" (aka at runtime?).

- Create an Application Class. @SpringBootApplication does a lot of the heavy lifting. It's proud to point out that there is no xml.
-A logger is needed for useful communication.

- This app can be built as an executable, or you can run it with gradle or Maven.

## [Accessing Data with JPA](https://spring.io/guides/gs/accessing-data-jpa)

Using annotation, you define Entity and within it associated Id with a GeneratedValue. Along with a constructor function for the object to be put into the Java Persistence API, you have the makings of a database, within Java. It seems that with this arrangement, interfaces will be instrumental in organizing and using the content going into and out of the database. And the database has methods to query and surface objects that are stored within it, either by its key value pairs or the unique Id created via the @GeneratedValue.


## [Comparing Repositories: CrudRepository, and Other Details](https://www.baeldung.com/spring-data-repositories)

but first! _JpaRepository_ has both full APIs of _CrudRepository_ and _PagingAndSortingRepository_! However if you don't need all that power, the others have their usefulness.

The @Repository annotation enables auto-generation of interface implementation (? ... huh?). Additional Spring Data JPA info and details are available [here](https://www.baeldung.com/the-persistence-layer-with-spring-data-jpa)

The _CrudRepository_ example is far too dense for me to make heads or tails of at this current time. But it does include the usual CRUD methods, so there is that.

_PagingAndSortingRepository_ is used for pagination, with properties for page size, current page number, and sorting capabilities.

_JpaRepository_ has all those and more. But due to its widespanning capabilities, might be "too much for it's own good" and expose too much than is advisable if not coded deliberately.
