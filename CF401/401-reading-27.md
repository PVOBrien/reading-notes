# Intents, Activities, and SharedPreferences

## [Tasks and Back Stack](https://developer.android.com/guide/components/activities/tasks-and-back-stack)
The following code blocks and quotes are attributed to [this page](https://developer.android.com/guide/components/activities/tasks-and-back-stack).
> "A task is a collection of activities that users interact with when performing a certain job."
The tasks are arranged in a _back stack_ - referring to the back button on android devices. This back stack starts from the Home screen. When the __Back__ button is pressed, it pops the most recent item on the stack. #LIFO.

## Managing Tasks

The ```<activity>``` element in the app manifest is where to control how and/or what is on the Back Stack. Within the ```<activity>``` the attributes to use to control the Back Stack behaviors are:

```
- taskAffinity
- launchMode
- allowTaskReparenting
- clearTaskOnLaunch
- alwaysRetainTaskState
- finishOnTaskLaunch
```

The following "principal intent flags" are also mentioned for use:

```
- FLAG_ACTIVITY_NEW_TASK
- FLAG_ACTIVITY_CLEAR_TOP
- FLAG_ACTIVITY_SINGLE_TOP
```

## Launch Modes

Either the ```<activity>``` or "principal intent flags" can be used for "launch modes". Launch modes "allow you to define how a new instance of an activity is associated with the current task.

Additionally, in connection with the launch mode, launch mode is in fact an attribute with different modes.

- "standard"
- "singleTop" (same as Intent flag ```FLAG_ACTIVITY_SINGLE_TOP```)
- "singleTask" (same as Intent flag ```FLAG_ACTIVITY_NEW_TASK```)
- "singleInstance"

```FLAG_ACTIVITY_CLEAR_TOP``` along with ```FLAG_ACTIVITY_NEW_TASK``` are commonly used to "relocate" an existing task to another and then being able to respond to the intent.

========
#### Handling Affinities is mentioned, that seems to allow for more granular prioritization and/or assignment of tasks with activities.
========

## [Android SharedPreferences](https://developer.android.com/training/data-storage/shared-preferences)
The following code blocks and quotes are attributed to [this page](https://developer.android.com/training/data-storage/shared-preferences).

> If you have a relatively small collection of key-values that you'd like to save, you should use the SharedPreferences APIs. A SharedPreferences object points to a file containing key-value pairs and provides simple methods to read and write them. Each SharedPreferences file is managed by the framework and can be private or shared.

These are accessed by ```getSharedPreferences()``` or ```getPreferences()``` and further commands such as ```getInt()``` or ```getString()``` for example.. In doing so, it states to use the standard Java package naming method (com.example.bar.foo.ETC). To access these properties, after the get...() method, writing to the file is used with putInt() or putString() then using either ```apply()``` or ```commit()``` to save them.
The differences between the two:

```apply()``` "changes the SharedPreferences immediately but writes the updates to disk asynchronously."
```commit()``` "is synchronous... avoid calling it from your main thread because it could pause your UI rendering."
