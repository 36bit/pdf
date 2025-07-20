# Chapter 7: Dialogs and the Dialog Manager

Dialog boxes are a crucial part of the Macintosh user interface. They provide a way for your application to communicate with the user and to get their input. In this chapter, you'll learn how to use the Dialog Manager to create and manage dialog boxes in your application.

## What are Dialog Boxes?

A dialog box is a special type of window that is used to display information to the user or to get input from the user. There are two main types of dialog boxes:

*   **Modal Dialog Boxes:** A modal dialog box is a dialog box that the user must dismiss before they can interact with any other part of your application. Modal dialog boxes are typically used for important messages or for getting required input from the user.
*   **Modeless Dialog Boxes:** A modeless dialog box is a dialog box that the user can interact with while still being able to interact with other parts of your application. Modeless dialog boxes are typically used for things like tool palettes or for displaying information that the user might want to refer to while they are working.

## The Dialog Manager

The Dialog Manager is a set of routines that allows you to create and manage dialog boxes. It handles all the low-level details of creating and managing dialog boxes, so you can focus on the content of your dialog boxes.

With the Dialog Manager, you can:

*   Create new dialog boxes
*   Show and hide dialog boxes
*   Get user input from dialog boxes
*   Handle dialog-related events

## Creating a Dialog Box

A common way to create a dialog box is to define it in a `'DLOG'` resource along with an associated `'DITL'` (dialog item list) resource.

*   The `'DLOG'` resource defines the dialog box itself, including its size, location, and window type.
*   The `'DITL'` resource defines the items in the dialog box, such as buttons, checkboxes, and static text.

Here's an example of how to create a modal dialog box from a resource:

```pascal
VAR
    myDialog:  DialogPtr;
    itemHit:   Integer;

myDialog := GetNewDialog(128, NIL, WindowPtr(-1));
ModalDialog(NIL, itemHit);
```

In this example, we're creating a new dialog box from a `'DLOG'` resource with the resource ID 128. We're then calling the `ModalDialog` procedure to display the dialog box and handle user interaction with it.

## Dialog Items

A dialog box can contain a variety of different items, including:

*   **Buttons:** You can create standard push buttons, checkboxes, and radio buttons.
*   **Static Text:** You can display static text that the user cannot edit.
*   **Editable Text:** You can create editable text fields that the user can type in.
*   **Icons:** You can display icons in your dialog boxes.
*   **Pictures:** You can display QuickDraw pictures in your dialog boxes.
*   **User Items:** You can create your own custom dialog items.

You define the items in a dialog box in a `'DITL'` resource. The `'DITL'` resource contains a list of all the items in the dialog box, along with their properties, such as their size, location, and type.

## Handling Dialog Events

When the user interacts with a dialog box, the Dialog Manager handles most of the events for you. For example, when the user clicks a button, the `ModalDialog` procedure will return the item number of the button that was clicked.

If you create a modeless dialog box, you'll need to handle dialog-related events in your event loop. You can use the `IsDialogEvent` function to determine whether an event is intended for a dialog box, and you can use the `DialogSelect` function to handle the event.

## Summary

In this chapter, you've learned how to use the Dialog Manager to create and manage dialog boxes in your application. You've seen how to create both modal and modeless dialog boxes, how to define dialog items in a `'DITL'` resource, and how to handle dialog-related events.

The next chapter explains how to interact with the Finder.
