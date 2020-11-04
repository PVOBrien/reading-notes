# [Notifications](401-reading-38.md)

## [Getting Started Hub](https://aws.amazon.com/sns/getting-started/)

SNS stands for Simple Notification Service, and there is also the Amazon SQS - Simple Queue Service. Pricing is dependent on quantity and included API calls, as well as where the message endpoints are.

[How to set up a mobile app](https://docs.aws.amazon.com/sns/latest/dg/mobile-push-send.html) </br>
Required:
- A set of credentials for connecting to one of the supported push notification services: ADM, APNs, Baidu, FCM, MPNS, or WNS.
- A device token or registration ID for the mobile app and device.
- Amazon SNS configured to send push notification messages to the mobile endpoints.
- A mobile app that is registered and configured to use one of the supported push notification services.

Go to the [Amazon SNS console](https://console.aws.amazon.com/sns/home) -> Mobile -> Push notifications -> Platform applications -> Create platform application -> "create an Application name" -> Push notification platform -> enter credentials.

Next, you'll need to build/code in a platform endpoint. The process (and the decent amount of code) can be found [here](https://docs.aws.amazon.com/sns/latest/dg/mobile-platform-endpoint.html) if the documentation is up to date.

