# Error Handling & Debugging

The chapter starts off by explaining "the stack". I have not thought of the stack in this setting, but it is a term well-known to Magic: The Gathering players (see [here](https://mtg.fandom.com/wiki/Stack)). The stack is the notion that there is something that happens, and any additional actions or effects that apply to that first item must be resolved in opposite order, such that the most last effect applied to the original action needs to be resolved first, and then work back down the other effects and actions until finally getting to that first action (hence, it "stacking"). However, due to errors (human or otherwise) some of the items or actions might not be able to be resolved, and hence an error is raised.

At this point, it is most likely that the error will be caught either within the script during it's preparation, or at it's execution. When it does happen, the console or code editor will reveal where the error is occurring and additional properties that will help to narrow it's cause (and come to a solution). Pages 459 through 461 describe the various errors that can be raised. Once you know what it is, you can either fix it, or help the system through it with try, catch, throw, and finally statements.

During the course of writing programs, the console can be useful to watch the progress of the script. Using console.info/warn/error, you can program the console to return values for you to observe what is happening. These can be grouped together by the use of console.group and then next console.info/warn/error/log. You can also have it print out content in tables of objects with value key pairs, or return a message if you set up conditions that evaluate to false. The debugger is able to walk through code, and can be coded in if expressions evaluate to false, at which point the debugger will begin, allowing you to go through the steps of what is returning. Try, Catch, and Finally code blocks allow you to customize and control how and what happens if code breaks while it is running.

POBrien (2020-06-12)

[Return to Code 201 Reading Notes](https://pvobrien.github.io/reading-notes/)
