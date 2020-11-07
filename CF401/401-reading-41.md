# [Intent Filters](https://developer.android.com/training/basics/intents/filters)

Adding ```<intent-filter>``` to your app's manifest (and including the corresponding acitivity element) allows it to show up as a option in the chooser dialogue. The intent needs an action (usually platform defined), data, and a category (although "CATEGORY_DEFAULT" is provided/used as a default unless otherwise provided). Android documentation (available via the top Header link) provides this example:
``` Java
<activity android:name="ShareActivity">
    <intent-filter>
        <action android:name="android.intent.action.SEND"/>
        <category android:name="android.intent.category.DEFAULT"/>
        <data android:mimeType="text/plain"/>
        <data android:mimeType="image/*"/>
    </intent-filter>
</activity>
```
which would handle either text or image data provided. A single intent can handle multiple actions (like both send and recieve).

When the intent comes back from an intent filter, you handle it by pulling it in from that intent, and then utilizing it as it is expected/programmed to. There is also the option to return a result, although I'm uncertain at the moment what that means. That it automatically just does something, and then says so? I'll have to find more examples to see this idea in action.
