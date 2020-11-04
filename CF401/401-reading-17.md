# Spring Authorization

## [Tutorial on OAuth](https://spring.io/guides/tutorials/spring-boot-oauth2)
Note: below code blocks found [here](https://spring.io/guides/tutorials/spring-boot-oauth2).

This is a tutorial slash template slash boilerplate walk through to get Spring Boot and OAuth2 working, complete with a link to the repo for it all to work, up to and including the app runs on localhost:8080 and requires either a github or google account to login (like any other login).

For a single sign on steps as follows:

1. Create a new Spring App project via the [Spring Boot Initialzr](https://start.spring.io) with the "Web" dependency as a starting point.
2. Create an index.html in the resources/static folder and include the following content in the header to prettify it (does not affect the OAuth, but they tell you this after the fact): 
```
    <link rel="stylesheet" type="text/css" href="/webjars/bootstrap/css/bootstrap.min.css"/>
    <script type="text/javascript" src="/webjars/jquery/jquery.min.js"></script>
    <script type="text/javascript" src="/webjars/bootstrap/js/bootstrap.min.js"></script>
```

and add this:
```
<dependency>
	<groupId>org.webjars</groupId>
	<artifactId>jquery</artifactId>
	<version>3.4.1</version>
</dependency>
<dependency>
	<groupId>org.webjars</groupId>
	<artifactId>bootstrap</artifactId>
	<version>4.3.1</version>
</dependency>
<dependency>
	<groupId>org.webjars</groupId>
	<artifactId>webjars-locator-core</artifactId>
</dependency>
```
to the projects pom.xml file.

3. Secure the Application.
- The Spring Security OAuth 2.0 Client start (add to pom.xml):
```
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-oauth2-client</artifactId>
</dependency>
```
and then "configure your app to use Github as the authentication provider". The page then leads you to three other pages (so this isn't a one page tutorial, tricksters).

4. Add New GitHub App
- First, add a New Github app.
  - Select "New OAuth App"
  - then "Register a new OAuth application" and follow the steps, be sure to include ```http://localhost:8080/login/oauth2/code/github``` as the Authorization callback URL
  - click _Register Application_
  
5. Configure ```application.yml```
to your application.yml
```
spring:
  security:
    oauth2:
      client:
        registration:
          github:
            clientId: github-client-id
            clientSecret: github-client-secret
# ...
```

6. Boot the Application @ http://localhost:8080

You just created a _Client Application_!

It goes on to show how to route an authenticated user through standard mapping annotations, with ```user(@AuthenticationPricincipal OAuth2User principal)```.
But to reconfigure some defaults that aren't best practice for this type of app, you extend WebSecurityConfigurerAdapter with:
```
@SpringBootApplication
@RestController
public class SocialApplication extends WebSecurityConfigurerAdapter {

    // ...

    @Override
    protected void configure(HttpSecurity http) throws Exception {
    	// @formatter:off
        http
            .authorizeRequests(a -> a
                .antMatchers("/", "/error", "/webjars/**").permitAll()
                .anyRequest().authenticated()
            )
            .exceptionHandling(e -> e
                .authenticationEntryPoint(new HttpStatusEntryPoint(HttpStatus.UNAUTHORIZED))
            )
            .oauth2Login();
        // @formatter:on
    }
}
```
Next up is a logout option, where a /logout route is created.
Thankfully, all the steps down below are - at the level this is communicating -- is a step-by-step, with a note of where larger, more indepth solutions are available. But they are still extensive, step-by-step, and complete with all relevant steps and code blocks for proper integration and next steps.
