# Chapter 13: Providing User Assistance

One of the hallmarks of a great Macintosh application is its ease of use. A big part of that is providing clear and accessible help to the user. In this chapter, you'll learn how to use the Help Manager to provide online help for your application.

## Balloon Help

The most common form of online help on the Macintosh is **Balloon Help**. Balloon Help provides small, descriptive balloons that appear when the user moves the cursor over an item on the screen. These balloons can provide a quick and easy way for users to get information about the different parts of your application's user interface.

## The Help Manager

The Help Manager is a set of routines that allows you to create and manage help balloons. It handles all the low-level details of drawing and managing help balloons, so you can focus on the content of your help messages.

With the Help Manager, you can:

*   Create help balloons for menus, dialog boxes, and windows
*   Display both text and pictures in your help balloons
*   Customize the appearance of your help balloons

## Creating Help Balloons

An effective way to create help balloons is to define them in help resources. Several resource types exist, each targeting a different part of the user interface:

*   `'hmnu'`: Defines help balloons for menus.
*   `'hdlg'`: Defines help balloons for items in a dialog box.
*   `'hrct'`: Defines help balloons for rectangular areas in a window.
*   `'hwin'`: Associates an `'hrct'` or `'hdlg'` resource with a window.
*   `'hfdr'`: Defines a help balloon for your application's icon in the Finder.
*   `'hovr'`: Overrides the default help balloons provided by the system.

You can create these resources using a resource editor like ResEdit. Once you've created your help resources, the Help Manager will automatically display the appropriate help balloon when the user moves the cursor over the corresponding item.

## Displaying Help Balloons Programmatically

You can also display help balloons programmatically by calling the `HMShowBalloon` function. This gives you more control over the appearance and behavior of your help balloons, but it's also more complex.

To display a help balloon programmatically, you first need to create a help message record. The help message record contains all the information about the help balloon, including its content, its tip location, and its variation code.

Here's an example of how to display a simple text-based help balloon:

```pascal
VAR
    myHelpMsg: HMMessageRecord;
    myTip:     Point;

myHelpMsg.hmmHelpType := khmmString;
myHelpMsg.hmmString := 'This is a help balloon.';
SetPt(myTip, 100, 100);
HMShowBalloon(myHelpMsg, myTip, NIL, NIL, 0, 0, kHMRegularWindow);
```

## Writing Good Help Messages

The key to providing good online help is to write clear, concise, and helpful help messages. Here are a few tips:

*   **Be brief:** Users don't want to read a lot of text in a help balloon. Get to the point quickly.
*   **Be specific:** Tell the user exactly what the item does.
*   **Use simple language:** Avoid technical jargon.
*   **Use graphics when appropriate:** Illustrations can clarify complex concepts.

## Summary

In this chapter, you've learned how to use the Help Manager to provide online help for your application. You've seen how to create help balloons for menus, dialog boxes, and windows. You've also learned how to write good help messages.

