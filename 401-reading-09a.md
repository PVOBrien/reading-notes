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

- HttpUrlConnection - the Java 8 class "to perform basic HTTP requests without the use of any additional libraries". This is found within the java.net package.

- Creating a Request - done so by using __openConnection()__ and the __requestMedho__ attribute is where the GET / PUT / POST / DELETE (and TRACE) is put.

- Adding Request Parameters - the best way to have this, is the example, screenshot from [here](https://www.baeldung.com/java-http-request).

![How to add request parameters](https://github.com/PVOBrien/reading-notes/blob/master/addRequestParams.png)

- Setting Request Headers - done by using __setRequestProperty()__. Headers are read by __getHeaderField()__.

- Configuring Timeouts - __setConnectTimeout()__ and __setReadTimeout()__ methods. They both take in milliseconds as args.

- Handling Cookies - packages _CookieManager_ and _HttpCookie_ add in managing cookies.

- Handling Redirects - use __setInstanceFollowRedirects()__.

- Reading the Response = first parse a response 
