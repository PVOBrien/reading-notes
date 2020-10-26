# [Espresso](https://developer.android.com/training/testing/espresso)

Espresso is built in to Android Studio to create automated testing, and aims to test when the app is "quiet" (for lack of a term that I know), when the app has nothing in the message queue, no ```Async Task``` instances executing, and all related idling resources are idle. At such a point, it then executes automated steps to perform tasks. Within these tasks, developers can have asserts so they can be assured the app is performing as expected (or, intended).

### [Espresso Testing Samples and Recipes](https://github.com/android/testing-samples)
- [ ] To be perused in depth at a later time.

## [Running a UI Test with Espresso Test Recorder](https://developer.android.com/training/testing/espresso)

NOTE: Turn off animations in your emulator or developer phone (or other Android testing environment).

Espresso makes UI interactions and assertions, and does so by running recorded tests, that are created by the tester. A tester tells the Espresso Recorder to run, at which point an Android Virtual Device spools up, the tester then starts recording the UI interactions, and when an assert is to be included, the tester enters that assert (or more than one), and either saves that test or continues on with that test). Repeat as necessary. 
