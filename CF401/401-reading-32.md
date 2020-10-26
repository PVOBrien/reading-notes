# Serverless and Amplify

## [Serverless Architecture](https://hackernoon.com/what-is-serverless-architecture-what-are-its-pros-and-cons-cc4b804022e9)

> “Focus on your application, not the infrastructure” (a good pullquote)

### Q. What is serverless?

A.
- "Serverless is a cloud computing execution model where the cloud provider dynamically manages the allocation and provisioning of servers..."
- "Serverless applications are event-driven cloud-based systems where application development rely solely on a combination of third-party services, client-side logic and cloud-hosted remote procedure calls (Functions as a Service)."

So it in a sense democratizes, and splits up the many pieces of a traditional server into their smaller pieces and then field those out to the best suited service for that part (or, they might just go w one of the big serverless providers and use all their tools).

Benefits include cost savings, less work for your IT/networking team, but you lose control and options (proprietary/private APIs throughout the service), and dpending on your dependencies, may or may not be possible, or require reworking your logic and routes. Also serverless solutions aren't the right setup for processor-intensive projects (there is a hard 300 second timeout limit, which seems pretty high for normal use cases). Interestingly, for scale the article states it's a toss up between the two; I thought since serverless scales for you, that it would be the clear winner.

### Functions as a Service (FaaS)

- They are "independent, server-side, logical functions." So they are able to work on/process discrete, individual, small pieces of work, and output them.
Faas is:
- stateless
- ephemerial
- event-triggered
- scalable
- fully managed by (cloud) vendor

#### Bottomline: You'll need to find out for yourself if serverless is the way to go for your use case (but the trend is moving to serverless atm).

## [AWS Amplify Kool-Aid](https://aws.amazon.com/amplify/)
- Is AWS Amplify the awesome-est? Amazon thinks so! Read about its awesomeness at the link above.

## [GraphQL Overview](https://docs.amplify.aws/cli/graphql-transformer/overview)

GraphQL is a type of noSQL (N.ot O.nly SQL), providing "a simple-to-use abstraction that helps you quickly create backends for your web and mobile applications on AWS." You need to run ```amplify init```  within the app's root folder IF YOU HAVEN'T ALREADY, and then run ```aimplify add api``` select GraphQL, and follow the steps. After creating your schema, run ```apmlify push``` in your CLI. If/when you need to update the GraphQL API, go to the project's ```back/api/~apiname~schema.graphql``` and edit accordingly. Then compile via CLI comman ```amplify api gql-compile``` then push with ```amplify push```. 
