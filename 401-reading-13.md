# Related Resources and Integration Testing

## Related Data Spring

1.  One-to-one relationship - w @OneToONe a one to one relationship can be created between two @Entities. Naming throughout must be intentional, otherwise JSON issues will arise.
- to make this work, interfaces must be implemented
    - public interface LibraryRepository extends CrudRepository<Library, Long> {}
    - public interface AddressRepository extends CrudRepository<Address, Long> {}
- at which an instance can be created and then used to turn it into json, and without an association, a GET request will return a null object.
- once both instances (?) are persistent, they can be related by an association resouce via URL parameters.

2. One-to-many - created and associated by using "/" routes to associate the related objects and properties with that "one" to "many" relationship and its objects.

3. Many-to-many - can be associated with other relationships by having the same route somewhere along the path.

4. This can all be tested.

## [Integration Testing](https://www.baeldung.com/integration-testing-in-spring)

__It's IMPORTANT__

- Really, the article does a great, thorough, and readable job of breaking down how to setup and build integration tests for server routes, expected returns, and some limitations and work-arounds to overcome them. I can see myself revisiting this page for reference, instead of trying to use the Spring documentation.
