# Chapter 10: The Desktop and the Desktop Manager

The desktop is the user's primary workspace on the Macintosh. It's where they store their files, folders, and applications. In this chapter, you'll learn how to use the Desktop Manager to get information about the items on the user's desktop.

## The Desktop Database

For each volume the Finder stores information about files and folders in a structure called the **desktop database**. It includes details such as:

*   The icons for each file and folder
*   The file types and creators for each file
*   The location of each application on the disk
*   The user comments for each file and folder

The Desktop Manager is a set of routines that allows you to access the information in the desktop database.

**Warning:** You should never modify the desktop database directly. The Desktop Manager provides routines for reading information from the database, but you should not use the routines for writing to the database unless you have a very good reason to do so. Modifying the desktop database can cause serious problems for the user, including data loss.

## Using the Desktop Manager

Before you can use the Desktop Manager, you need to make sure that the target disk has a desktop database. You can do this by calling the `PBHGetVolParms` function.

Once you've verified that a desktop database exists, you can use the `PBDTGetPath` function to get a reference number for the database. You'll need to provide this reference number when you call other Desktop Manager routines.

## Getting Information from the Desktop Database

The Desktop Manager provides several routines for getting information from the desktop database:

*   `PBDTGetIcon`: This function returns the icon for a file of a given type and creator.
*   `PBDTGetIconInfo`: This function returns information about the different icon types that are available for a given application.
*   `PBDTGetAPPL`: This function returns the name and location of the application that created a file.
*   `PBDTGetComment`: This function returns the user's comment for a file or folder.

Here's an example of how to get the user's comment for a file:

```pascal
VAR
    myDTPB:    DTPBRec;
    myComment: Handle;
    myErr:     OSErr;

myComment := NewHandle(200);
myDTPB.ioNamePtr := @myFileName;
myDTPB.ioVRefNum := myVRefNum;
myDTPB.ioDTBuffer := myComment;
myErr := PBDTGetComment(@myDTPB, FALSE);
```

In this example, we're getting the comment for a file named `myFileName` on the volume `myVRefNum`. The comment is returned in the `myComment` handle.

## Summary

In this chapter, you've learned how to use the Desktop Manager to get information about the files and folders on the user's desktop. You've seen how to get information about icons, file types, and user comments. You've also been warned about the dangers of modifying the desktop database directly.

This concludes Part 2 of this book. In Part 3, we'll explore some of the more advanced features of the Macintosh Toolbox.
