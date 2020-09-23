# WRRC and Java

## [High-level HTTP](https://dev.to/dangolant/things-i-brushed-up-on-this-week-the-http-request-lifecycle-)

Local Processing

- Your computer deciphers your URL, and adds (in the background) the rest of the necessary details to send out a request
- It checks its local cache to see if it can find the request there, and put less burden on the system elsewhere. If it cannot...
- It sends out a Domain Name Server (DNS) request.
- Once it finds it (or not, and so ends this process) it connects to the DNS via a transport layer protocol via a TCP connection, and communication can now occur.
- Now: the http request of the URL goes to the DNS to resolve it.
- The communication is ongoing so long as there is a connection.
- Upon all completion (and a brief timeout) the communication shuts down, and both sides clean up various details, and both are ready to make additional calls / requests.

## [Java HTTP Request example](https://www.baeldung.com/java-http-request)

### HttpUrlConnection - the Java 8 class "to perform basic HTTP requests without the use of any additional libraries". This is found within the java.net package.

### Creating a Request - done so by using __openConnection()__
