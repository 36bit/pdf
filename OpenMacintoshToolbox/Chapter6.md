# Chapter 6: Controls and the Control Manager

Controls are the interactive elements of the Macintosh user interface. They are the buttons, checkboxes, scroll bars, and other objects that users can manipulate to control your application. In this chapter, you'll learn how to use the Control Manager to create and manage controls in your application.

## What are Controls?

A control is a graphical object that the user can manipulate with the mouse to cause an action, to change a setting, or to input a value. Here are some of the most common types of controls:

*   **Buttons:** A button is a control that the user can click to cause an immediate action. For example, the "OK" and "Cancel" buttons in a dialog box are buttons.
*   **Checkboxes:** A checkbox is a control that allows the user to turn an option on or off. A checkbox displays an "X" when the option is on.
*   **Radio Buttons:** Radio buttons are used to select one option from a group of mutually exclusive options. When the user selects one radio button, any other radio button in the group is deselected.
*   **Scroll Bars:** A scroll bar is a control that allows the user to scroll through the content of a window.
*   **Pop-up Menus:** A pop-up menu is a control that displays a list of choices when the user clicks on it.

## The Control Manager

The Control Manager is a set of routines that allows you to create and manage controls. It handles all the low-level details of drawing and managing controls, so you can focus on the actions that your controls perform.

With the Control Manager, you can:

*   Create new controls
*   Show and hide controls
*   Move and resize controls
*   Get and set the value of a control
*   Handle control-related events

## Creating a Control

You can create a new control in two ways:

*   **From a resource:** You can define a control in a `'CNTL'` resource and then use the `GetNewControl` function to create the control from the resource. This is the easiest way to create a control, and it's the recommended approach for most applications.
*   **Programmatically:** You can also create a control programmatically by calling the `NewControl` function. This gives you more control over the control's appearance and behavior, but it's also more complex.

Here's an example of how to create a button from a `'CNTL'` resource:

```pascal
VAR
    myControl: ControlHandle;
    myWindow:  WindowPtr;

myControl := GetNewControl(128, myWindow);
```

In this example, we're creating a new control from a `'CNTL'` resource with the resource ID 128. The second parameter is a pointer to the window that the control will be in.

## Handling Control Events

When the user clicks on a control, the `WaitNextEvent` function returns a `mouseDown` event. Your application should then call the `FindControl` function to determine which control the user clicked.

If the user clicked on a control, `FindControl` returns a handle to the control and a part code that indicates which part of the control was clicked. Your application should then call the `TrackControl` function to handle the user's interaction with the control.

`TrackControl` tracks the mouse as the user holds down the mouse button, highlighting the control and performing any necessary actions. For example, if the user clicks on a scroll bar, `TrackControl` will scroll the window as the user drags the scroll thumb.

Here's how you might handle a control event in your event loop:

```pascal
VAR
    myControl: ControlHandle;
    partCode:  Integer;

...

partCode := FindControl(myEvent.where, myWindow, myControl);
IF myControl <> NIL THEN
BEGIN
    IF TrackControl(myControl, myEvent.where, NIL) <> 0 THEN
        HandleControlAction(myControl);
END;
```

The `HandleControlAction` procedure would then use the control handle to determine which control was clicked and then perform the appropriate action.

## Custom Controls

The Control Manager provides a set of standard control definition functions that define the appearance and behavior of the standard controls. You can also create your own custom controls by writing your own control definition function.

A control definition function is a code resource of type `'CDEF'` that is responsible for drawing a control and handling user interaction with the control. By writing your own control definition function, you can create controls with any appearance and behavior you can imagine.

## Summary

In this chapter, you've learned how to use the Control Manager to create and manage controls in your application. You've seen how to create controls from resources, how to handle control-related events, and how to create custom controls.

In the next chapter, we'll learn about dialog boxes and the Dialog Manager.
