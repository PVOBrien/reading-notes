# Android Application Fundamentals

## The Basics

  Every android app is actually running as a user in its own VM. An app can be coded in Kotlin, Java, or C++. It can be setup that two apps share the same user ID (account) in order to better coordinate resources and files. An app can request access to device data (including the devices hardward input/output).

## App Components
Note: below quotes attribution is from [this page](https://developer.android.com/guide/components/fundamentals)

- Activities
> "A single screen with a user interface." Where/how users interact with an android app. Activities can be implimented as subclasses of the Activity class.
- Services
> "General-purpose entry point for keeping an app running in the background." Think music players, or runner tracker apps that use gps. Can provide APIs for other apps/services to also plug into.
- Broadcast Receivers
> "A component that enables the system to deliver events to the app outside of a regualr user flow." Can originate from the system or from apps for many reason.
- Content Providers
> "A content provider manages a shared set of app data that you can store in the file system... or any other persistent storage location that your app can access."

## Activating Components

Excepting content providers, they are activated by an _intent_ that then " 'binds' components to each other at runtime". The _intent_ defines the action - something like POST/GET/PUT/DELETE. Content providers work via a __ContentResolver__ that handles the direct transactions, providing a layer of abstraction for security purposes.

## Manifest File (where all components of an app are declared)

### Declaring Components

The manifest file is a .xml file listing (declaring) the app's components. This includes:

- Activities
- Services
- Broadcast Receivers
- Content Providers

### Component Capabilities - what components can/are allowed/are programmed to is stated do here.

### App requirements - if there is any software/hardware requirements in order to run the app.

## App Resources - everything else that isn't code that is used to run the software (e.g. media and visual presentation .xml)
