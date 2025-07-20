# Chapter 11: Creating Custom Interface Elements

The Macintosh Toolbox provides a rich set of standard user interface elements, such as buttons, checkboxes, and scroll bars. But sometimes, you need to create your own custom interface elements to meet the specific needs of your application. In this chapter, you'll learn how to use the List Manager, the Icon Utilities, and the Control Panel framework to create your own custom interface elements.

## The List Manager

The List Manager is a set of routines that allows you to create and manage scrollable lists of items. You can use the List Manager to create simple one-column lists of text, or you can create complex multicolumn lists with graphical elements.

To create a list, you first need to define the list in a `'LDEF'` resource. The `'LDEF'` resource defines the appearance and behavior of the list. You can then use the `LNew` function to create the list from the resource.

Once you've created a list, you can use the List Manager routines to:

*   Add and remove items from the list
*   Get and set the selection
*   Handle list-related events

## The Icon Utilities

The Icon Utilities are a set of routines that allow you to draw and manipulate icons. You can use the Icon Utilities to draw icons in your windows, dialog boxes, and menus.

To draw an icon, you first need to get a handle to the icon data. You can do this by calling the `GetIcon` function or the `GetCIcon` function. Once you have a handle to the icon, you can use the `PlotIcon` function or the `PlotCIcon` function to draw the icon.

The Icon Utilities also provide routines for:

*   Creating icon suites, which are collections of related icons
*   Performing hit-testing on icons
*   Converting icon masks to regions

## Control Panels

A control panel is an executable file of type `'cdev'`. When opened from the Finder it appears as a modeless dialog box that lets the user adjust settings for a system-wide feature, such as speaker volume or mouse tracking speed.

You can create your own control panels to provide a user interface for the features in your application. To create a control panel, you need to create a `'cdev'` resource. The `'cdev'` resource contains the code that implements the control panel.

When the user opens your control panel, the Finder will load your `'cdev'` resource into memory and then call your control panel's main function. Your main function is responsible for handling events and for managing the controls in your control panel.

## Summary

In this chapter, you've learned how to use the List Manager, the Icon Utilities, and the Control Panel framework to create your own custom interface elements. You've seen how to create scrollable lists of items, how to draw and manipulate icons, and how to create your own control panels.

The next chapter explains how to extend system capabilities with the Component Manager and the Translation Manager.
