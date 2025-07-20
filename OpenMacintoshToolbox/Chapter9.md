# Chapter 9: The Scrap Manager and Data Sharing

One of the most powerful features of the Macintosh is the ability to easily share data between different applications. This is made possible by the **Scrap Manager**, which provides a simple and consistent way for applications to implement cut, copy, and paste functionality. In this chapter, you'll learn how to use the Scrap Manager to share data with other applications.

## The Clipboard

The **Clipboard** is the user's view of the data that is currently in the scrap. When the user chooses the Cut or Copy command in your application, you should place the selected data on the Clipboard. When the user chooses the Paste command, you should get the data from the Clipboard and insert it into the current document.

The Clipboard can contain data in multiple formats. For example, if the user copies a piece of styled text, you could place both a plain text version and a styled text version of the data on the Clipboard. This allows other applications to choose the format that they can best handle.

## The Scrap Manager

The Scrap Manager is a set of routines that allows you to read from and write to the scrap. It handles all the low-level details of managing the scrap, so you can focus on the data that you want to share.

With the Scrap Manager, you can:

*   Get information about the contents of the scrap
*   Read data from the scrap
*   Write data to the scrap

## Writing to the Scrap

To write data to the scrap, you first need to clear the current contents of the scrap by calling the `ZeroScrap` function. Then, you can use the `PutScrap` function to write your data to the scrap.

You can call `PutScrap` multiple times to write data in multiple formats. You should always write the most descriptive format first. For example, if you're writing styled text to the scrap, you should write the styled text format first, followed by the plain text format.

Here's an example of how to write a string to the scrap:

```pascal
VAR
    myString: Str255;
    myErr:    OSErr;

myString := 'Hello, world!';
myErr := ZeroScrap;
IF myErr = noErr THEN
    myErr := PutScrap(Length(myString), 'TEXT', @myString[1]);
```

## Reading from the Scrap

To read data from the scrap, you can use the `GetScrap` function. You simply provide a handle to a memory location where the data should be placed and the scrap format type that you want to get.

If the requested format is not available, `GetScrap` will return an error. You should always be prepared to handle this error by trying to get the data in a different format. For example, if you're trying to get styled text from the scrap and the styled text format is not available, you should then try to get the plain text format.

Here's an example of how to read a string from the scrap:

```pascal
VAR
    myHandle: Handle;
    myLength: LongInt;
    myOffset: LongInt;

myHandle := NewHandle(0);
myLength := GetScrap(myHandle, 'TEXT', myOffset);
IF myLength > 0 THEN
    // The data was successfully read
ELSE
    // The 'TEXT' format was not available
```

## Suspend and Resume Events

When your application is switched to the background, you will receive a suspend event. If you are using a private scrap, you must copy the contents of your private scrap to the public scrap at this time. This ensures that the user can paste the data into another application.

When your application is switched back to the foreground, you will receive a resume event. At this time, you should check to see if the contents of the public scrap have changed. If they have, you should copy the new data to your private scrap.

## Summary

In this chapter, you've learned how to use the Scrap Manager to implement cut, copy, and paste functionality in your application. You've seen how to write data to the scrap in multiple formats, how to read data from the scrap, and how to handle suspend and resume events.

In the next chapter, we'll learn about the Desktop Manager and how to interact with the desktop.
