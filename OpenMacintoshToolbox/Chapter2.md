# Chapter 2: Resources and the Resource Manager

In the last chapter the concept of resources was introduced as a way to separate data and code from an application's main executable. This chapter examines resources in more detail and explains how the Resource Manager provides access to them.

## What are Resources?

A resource is a piece of data or code that is stored in a special "resource fork" of a file, separate from the file's "data fork". This separation is a cornerstone of Macintosh programming and offers several key advantages:

*   **Localization:** By storing text and other language-dependent elements in resources, you can easily translate your application into different languages without having to modify your source code.
*   **Flexibility:** You can change the appearance of your application's user interface by simply editing its resources. This means you can create different "skins" or themes for your application, or even allow users to customize the interface to their liking.
*   **Efficiency:** The Resource Manager can load resources into memory on an as-needed basis, which can help to reduce your application's memory footprint.

## The Resource Fork and the Data Fork

Every Macintosh file has two parts, or "forks":

*   **Data Fork:** This is where the main data of the file is stored. For a word processing document, this would be the text of the document itself. For an image file, this would be the pixel data for the image.
*   **Resource Fork:** This is where the file's resources are stored. This can include things like menus, dialog boxes, icons, sounds, and even executable code.

Your application can read from and write to both the data fork and the resource fork. Typically, you'll use the File Manager to work with the data fork and the Resource Manager to work with the resource fork.

## Resource Types and IDs

Every resource has a **resource type** and a **resource ID**.

*   **Resource Type:** This is a four-character code that identifies the type of data that the resource contains. For example, the resource type for a menu is `'MENU'`, and the resource type for an icon is `'ICON'`. There are many standard resource types, and you can also define your own.
*   **Resource ID:** This is a unique number that identifies a specific resource of a given type. For example, you might have several menus in your application, each with its own unique resource ID.

You can also give a resource a name, but it's more common to refer to resources by their type and ID.

## The Resource Manager

The Resource Manager is a set of routines that allows you to work with resources. It provides a simple and powerful way to:

*   Create, read, write, and delete resources
*   Get information about resources
*   Manage the loading and unloading of resources from memory

The Resource Manager handles the low-level details of working with resource forks, so you don't have to worry about things like file offsets and data structures.

### The Resource Search Path

When the Resource Manager is asked to retrieve a resource it follows a defined **resource search path**. The search begins with the resource forks of any files opened by the application, checked in the reverse order in which they were opened. If the resource is not located there, the Manager looks in the application's resource fork and finally in the System file. This ordering allows document-specific resources to override those in the application, and application resources to override those provided by the system.

### Creating a Resource

You can create resources in several ways:

*   **Using a resource editor:** Tools like ResEdit allow you to create and edit resources visually. This approach works well for user interface elements such as menus, dialog boxes, and icons.
*   **Using a resource compiler:** You can also create resources by writing a textual description of the resource in a file and then using a resource compiler like Rez to compile the description into a resource.
*   **Using the Resource Manager:** You can also create and modify resources programmatically using the Resource Manager routines.

### Reading a Resource

To read a resource into memory, you can use the `GetResource` function. You simply provide the resource type and ID, and `GetResource` will return a handle to the resource data.

```pascal
VAR
    myMenuHandle: MenuHandle;

myMenuHandle := MenuHandle(GetResource('MENU', 128));
```

In this example, we're getting a handle to a menu resource with the resource ID 128. We're then casting the handle to a `MenuHandle` so that we can use it with the Menu Manager routines.

## Common Resource Types

Here are some of the most common resource types you'll encounter:

*   `'MENU'`: Defines a menu and its items.
*   `'WIND'`: Defines a window.
*   `'DLOG'`: Defines a dialog box.
*   `'DITL'`: Defines the items in a dialog box.
*   `'CNTL'`: Defines a control, such as a button or a scroll bar.
*   `'ICON'`: Defines a black-and-white icon.
*   `'cicn'`: Defines a color icon.
*   `'STR '`: Defines a single string of text.
*   `'STR#'`: Defines a list of strings.
*   `'snd '`: Defines a sound.
*   `'CODE'`: Defines a segment of executable code.

Many of these resource types are described in greater detail in later chapters.

## Summary

In this chapter, you've learned about the fundamental role that resources play in Macintosh programming. You've seen how resources allow you to separate data and code from your application, making it easier to localize, customize, and maintain your code. You've also been introduced to the Resource Manager, the powerful set of routines that allows you to work with resources.

The next chapter introduces the Event Manager and explains how to respond to user actions such as mouse clicks and key presses.
