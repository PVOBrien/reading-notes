# Real Time Messaging with Websockets

Get this tutorial on the road jumping over to [Spring Initializr](https://start.spring.io), and it requires the Websocket dependency included.
Furthermore, you'll need to add in to your build.gradle so that it includes the following:
```
plugins {
	id 'org.springframework.boot' version '2.3.2.RELEASE'
	id 'io.spring.dependency-management' version '1.0.8.RELEASE'
	id 'java'
}

group = 'com.example'
version = '0.0.1-SNAPSHOT'
sourceCompatibility = '1.8'

repositories {
	mavenCentral()
}

dependencies {
	implementation 'org.springframework.boot:spring-boot-starter-websocket'
	implementation 'org.webjars:webjars-locator-core'
	implementation 'org.webjars:sockjs-client:1.0.2'
	implementation 'org.webjars:stomp-websocket:2.3.3'
	implementation 'org.webjars:bootstrap:3.3.7'
	implementation 'org.webjars:jquery:3.1.1-1'
	testImplementation('org.springframework.boot:spring-boot-starter-test') {
		exclude group: 'org.junit.vintage', module: 'junit-vintage-engine'
	}
}

test {
	useJUnitPlatform()
}
```

With these environmental considerations in place, it is time to create the [STOMP](https://en.wikipedia.org/wiki/Streaming_Text_Oriented_Messaging_Protocol) (aka Streaming Text Oriented Messaging Protocol).

Firstly, make your Class for your message. This will include a name, and body, and set the standard getters, setters, and constructor (plus, make a default constructor for any @AUTOWIRE purposes). Then create another class (no name suggested) with a content property and the getter for it.

Then it decides that it'll use the Jackson JSON library for kicks. Why? What does Jackson do? _go there if you want more info_.

Then you wire up a controller file for GreetingController to handle the route, as well as configure Spring for STOMP messaging, and create an html page with the proper routes and tag properties in the forms. Do note that the html will need
```html
    <link href="/webjars/bootstrap/css/bootstrap.min.css" rel="stylesheet">
    <script src="/webjars/jquery/jquery.min.js"></script>
    <script src="/webjars/sockjs-client/sockjs.min.js"></script>
    <script src="/webjars/stomp-websocket/stomp.min.js"></script>
```
The tutorial then blazes through the actual execution of the app ("it just works!") and then you can make it run.
