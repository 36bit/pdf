# Chapter 3: Events and the Event Manager

At the heart of every Macintosh application is the **event loop**. Unlike traditional programs that run from top to bottom, Macintosh applications are **event-driven**. This means they spend most of their time waiting for the user to do something, and then they respond to those actions. In this chapter, you'll learn about the different types of events that can occur and how to use the Event Manager to handle them.

## The Event-Driven Model

Imagine a traditional command-line program. It starts, it performs a series of tasks in a predefined order, and then it exits. A Macintosh application, on the other hand, is more like a reactive system. It sits and waits for events to occur, and then it responds to those events. This is what makes Macintosh applications so interactive and user-friendly.

An **event** is any action that your application needs to respond to. This can include things like:

*   The user clicking the mouse
*   The user pressing a key on the keyboard
*   The user inserting a disk
*   A window being moved or resized
*   Your application being switched to the background

The Event Manager is responsible for detecting these events and reporting them to your application. Your application's main task is to get events from the Event Manager and then dispatch them to the appropriate parts of your code for handling.

## The Event Loop

The core of every Macintosh application is the **event loop**. The event loop is a simple loop that repeatedly gets an event from the Event Manager and then calls the appropriate routine to handle that event. Here's what a basic event loop looks like in Pascal:

```pascal
VAR
    myEvent: EventRecord;
    done:    Boolean;

done := FALSE;
WHILE NOT done DO
BEGIN
    IF WaitNextEvent(everyEvent, myEvent, 0, NIL) THEN
    BEGIN
        CASE myEvent.what OF
            mouseDown:
                HandleMouseDown(myEvent);
            keyDown, autoKey:
                HandleKeyDown(myEvent);
            updateEvt:
                HandleUpdate(myEvent);
            // etc.
        END;
    END;
END;
```

Let's break down this code:

*   `WaitNextEvent`: This is the key function in the event loop. It gets the next available event from the Event Manager and returns it in the `myEvent` parameter. If there are no events waiting, `WaitNextEvent` will wait until one occurs.
*   `everyEvent`: This is a constant that tells `WaitNextEvent` that we're interested in all types of events.
*   `myEvent`: This is an `EventRecord`, which is a data structure that contains information about the event, such as its type, the location of the mouse, and the state of the modifier keys.
*   `myEvent.what`: This field of the `EventRecord` contains a code that identifies the type of event.
*   `CASE myEvent.what OF`: This is a `CASE` statement that dispatches the event to the appropriate handler based on its type.

## Types of Events

The Event Manager can report many different types of events. Here are some of the most common ones:

*   `mouseDown`: The user has pressed the mouse button.
*   `mouseUp`: The user has released the mouse button.
*   `keyDown`: The user has pressed a key on the keyboard.
*   `keyUp`: The user has released a key on the keyboard.
*   `autoKey`: The user is holding down a key, and the key is repeating.
*   `updateEvt`: A window needs to be redrawn.
*   `diskEvt`: A disk has been inserted.
*   `activateEvt`: A window has been activated or deactivated.
*   `osEvt`: An operating system event has occurred, such as your application being switched to the background.
*   `kHighLevelEvent`: A high-level event has occurred, such as an Apple event.

We'll learn more about how to handle these different types of events in the chapters to come.

## The Event Record

The `EventRecord` is a data structure that contains all the information you need to know about an event. Here's what it looks like:

```pascal
TYPE
    EventRecord = RECORD
        what:      Integer;      {The type of event}
        message:   LongInt;      {Additional information about the event}
        when:      LongInt;      {The time the event occurred, in ticks}
        where:     Point;        {The location of the mouse, in global coordinates}
        modifiers: Integer;      {The state of the modifier keys}
    END;
```

*   `what`: We've already seen this field. It tells you the type of event.
*   `message`: This field contains additional information about the event. For example, for a `keyDown` event, this field contains the character code and the key code for the key that was pressed.
*   `when`: This field contains the time the event occurred, in ticks since the system was started. A tick is approximately 1/60 of a second.
*   `where`: This field contains the location of the mouse at the time the event occurred, in global coordinates.
*   `modifiers`: This field contains a bitmask that indicates the state of the modifier keys (Shift, Command, Option, and Control) at the time the event occurred.

## Summary

In this chapter, you've learned about the event-driven model of Macintosh programming and the central role of the event loop. You've also been introduced to the Event Manager, the different types of events, and the `EventRecord` data structure.

In the next chapter, we'll learn how to create and manage windows, which are the primary way that users interact with your application.
