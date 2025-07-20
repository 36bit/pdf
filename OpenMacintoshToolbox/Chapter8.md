# Chapter 8: The Finder Interface

The Finder is the heart of the Macintosh user experience. It's the application that the user interacts with to manage files, launch applications, and organize their work. In this chapter, you'll learn how your application can interact with the Finder to provide a seamless and integrated experience for the user.

## The Finder and Your Application

The Finder is responsible for displaying your application's icon and for launching your application when the user double-clicks on its icon or on a document that it created. To do this, the Finder needs to know some basic information about your application, such as its name, its icon, and the types of documents it can open.

You provide this information to the Finder by including a set of special resources in your application's resource fork. These resources are known as the **Finder resources**.

## Finder Resources

There are several different types of Finder resources, but the most important ones are:

*   **Signature Resource:** The signature resource is a resource of type `'STR '` that contains your application's unique four-character signature. The Finder uses this signature to identify your application and to associate it with the documents it creates.
*   **Bundle Resource (`'BNDL'`):** The bundle resource is the main Finder resource. It groups together all the other Finder resources for your application, including its signature, its icon, and its file references.
*   **File Reference Resource (`'FREF'`):** A file reference resource associates a file type with your application. For example, you would create a `'FREF'` resource to tell the Finder that your application can open documents of type `'TEXT'`.
*   **Icon List Resource (`'ICN#'`):** An icon list resource contains the black-and-white icon and mask for your application or for a document that it creates.
*   **Icon Family:** As we've discussed in previous chapters, an icon family is a set of icons that represent a single object at different sizes and bit depths. You should provide a complete icon family for your application and for each type of document it creates.

## Creating Finder Resources

You can create Finder resources using a resource editor like ResEdit. When you create a new application, you should create a signature resource, a bundle resource, and at least one file reference resource. You should also create a complete icon family for your application and for each type of document it creates.

## Handling Finder Events

When the user interacts with your application's icon or with a document that it created, the Finder sends your application a set of required Apple events. Your application must be able to handle these events.

The four required Apple events are:

*   **Open Application (`'oapp'`):** The Finder sends this event to your application when the user double-clicks on its icon. In response to this event, you should open a new, untitled document.
*   **Open Documents (`'odoc'`):** The Finder sends this event to your application when the user double-clicks on one or more documents that it created. In response to this event, you should open the specified documents.
*   **Print Documents (`'pdoc'`):** The Finder sends this event to your application when the user selects one or more documents in the Finder and chooses the Print command. In response to this event, you should print the specified documents.
*   **Quit Application (`'quit'`):** The Finder sends this event to your application when the user chooses the Shut Down or Restart command. In response to this event, you should quit your application, giving the user an opportunity to save any unsaved changes.

Handling Apple events is covered in a later chapter.

## Summary

In this chapter, you've learned how your application can interact with the Finder. You've seen how to create the Finder resources that the Finder uses to display your application's icon and to associate documents with your application. You've also learned about the four required Apple events that your application must be able to handle.

The next chapter describes the Scrap Manager and explains how to share data with other applications.
