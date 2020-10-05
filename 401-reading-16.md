# Spring Authentification

## [Spring Security Overview](https://spring.io/guides/topicals/spring-security-architecture)

Filters. I see this show up in the logs whenever I hit the play button.

"The main strategy interface for authentication is ```AuthenticationManager``` (AM) and the class opens with
```
public interface AuthenticationManager {

  Authentication authenticate(Authentication authentication)
    throws AuthenticationException;

}
```

and can accomplish 3 things in ```authenticate()```:
1. return an Authentication (usually true) if properfly verified.
2. throw an AuthenticationException if input is invalidated. (This is a runtime exception.)
3. return null if it's uncertain.

The implementation of AM is commonly ProviderManager (PM), which seems to be the AM with the added benefit to take in different Authentication types (if supported).

Then the PM begins/is able to delegate to mulitple resources, with the ProviderManager as a fallback/catchall.

There are many options at this stage to customize the AM/PM to act as desired. Once that authentication is complete we go to...
#### "Authorization"

which centers around ```AccessDecisionManager```. There is a lot happening here, but of note to me, it is "```Affirmative Based``` meaning once a user returns true/authenticated then access (at whatever level that is) is granted, and that access is managed by ConfigAttributes - which is supported by an ```AccessDecisionVoter```.

Web Security (from spring.io guide)
![Web Security Diagram](https://github.com/spring-guides/top-spring-security-architecture/raw/master/images/filters.png)

Servlets are the "end of the road for a wrrc, in the since that after it's properly handshaked, then the filters applied, and then the correctly chosen servlet is sent back. __Spring Security__ is a filter in that chain, and furthermore all it's filters go into a ```FilterChainProxy```. The FilterChainProxy can be very customized, tailored.

The rabbit hole is deep at this level, mentions of actuators, additional ```@Bean```s, both Web security _and_ method security, and the ability/necessity to use @Async at times.

## [Spring Auth Cheat Sheet](https://github.com/codefellows/seattle-java-401d2/blob/master/SpringAuthCheatSheet.md)

This cheat sheet boils down and removes a good 75% of the confusion of the Spring.io guide., boiling it down to 6 steps. Much more readable and understandable for the base level of using the service.
