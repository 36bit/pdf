# Chapter 5: Menus and the Menu Manager

Menus are a fundamental part of the Macintosh user interface. They provide a consistent and predictable way for users to access your application's commands and features. In this chapter, you'll learn how to use the Menu Manager to create, manage, and handle menus in your application.

## The Anatomy of a Menu

A Macintosh menu is a list of commands or options that appears when the user clicks on a menu title in the menu bar. Here are the main parts of a menu:

*   **Menu Bar:** The menu bar is the horizontal bar at the top of the screen that contains the menu titles.
*   **Menu Title:** A menu title is the name of a menu, such as "File" or "Edit".
*   **Menu Item:** A menu item is a command or option in a menu, such as "Open" or "Save".
*   **Submenu:** A submenu is a menu that appears when the user chooses a menu item that has a hierarchical menu attached to it.

## The Menu Manager

The Menu Manager is a set of routines that allows you to create and manage menus. It handles all the low-level details of drawing and managing menus, so you can focus on the commands and features in your menus.

With the Menu Manager, you can:

*   Create new menus
*   Add and remove menu items
*   Enable and disable menu items
*   Check and uncheck menu items
*   Handle menu-related events

## Creating a Menu

The easiest way to create a menu is to define it in a `'MENU'` resource. A `'MENU'` resource contains all the information about a menu, including its title, its items, and their properties.

Here's an example of a `'MENU'` resource for a simple File menu:

```pascal
resource 'MENU' (128, "File") {
    128,
    textMenuProc,
    allEnabled,
    enabled,
    "File",
    {
        "New", noIcon, "N", noMark, plain;
        "Open...", noIcon, "O", noMark, plain;
        "-", noIcon, noKey, noMark, plain;
        "Save", noIcon, "S", noMark, plain;
        "Quit", noIcon, "Q", noMark, plain
    }
};
```

Once you've defined your menus in resources, you can create a menu bar by calling the `GetNewMBar` function. This function gets a menu bar resource (`'MBAR'`) and creates the menu bar and all the menus in it.

## Handling Menu Selections

When the user chooses a menu item, the `WaitNextEvent` function returns a `mouseDown` event. Your application should then call the `MenuSelect` function to handle the menu selection.

`MenuSelect` tracks the mouse as the user moves it through the menus, highlighting menu items and displaying submenus as needed. When the user releases the mouse button, `MenuSelect` returns a long integer that contains the menu ID and the menu item number of the selected item.

Here's how you might handle a menu selection in your event loop:

```pascal
VAR
    menuResult: LongInt;

...

menuResult := MenuSelect(myEvent.where);
HandleMenuChoice(menuResult);
```

The `HandleMenuChoice` procedure would then use the menu ID and menu item number to determine which command the user chose and then execute the appropriate action.

## Standard Menus

Every Macintosh application should have at least three standard menus:

*   **Apple Menu:** The Apple menu is the first menu on the left side of the menu bar. It should contain an "About" item that displays information about your application, as well as any other items that the user has placed in the Apple Menu Items folder.
*   **File Menu:** The File menu should contain commands for working with documents, such as "New", "Open", "Save", and "Print". It should also contain a "Quit" command to exit the application.
*   **Edit Menu:** The Edit menu should contain commands for editing text and other data, such as "Undo", "Cut", "Copy", and "Paste".

You should create these standard menus in your application, and you should follow the standard Macintosh Human Interface Guidelines for their content and organization.

## Summary

In this chapter, you've learned how to use the Menu Manager to create and manage menus in your application. You've seen how to define menus in resources, how to handle menu selections, and how to create the standard Apple, File, and Edit menus.

In the next chapter, we'll learn about controls and the Control Manager.
