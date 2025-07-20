# Chapter 12: Extending System Capabilities

The Macintosh operating system is designed to be extensible. This means that you can add new features and capabilities to the system without having to modify the operating system itself. In this chapter, you'll learn how to use the Component Manager and the Translation Manager to extend the capabilities of the Macintosh operating system.

## The Component Manager

The Component Manager is a set of routines that allows you to find and use software components at run time. A **component** is a piece of code that provides a defined set of services to one or more clients. For example, a component might provide image compression or decompression services.

By using the Component Manager, you can write your application to a standard interface, and then let the Component Manager find and load the appropriate component at run time. This makes it easy to add new features to your application without having to recompile it. It also allows you to take advantage of new components as they become available.

To use a component, you first need to find the component using the `FindNextComponent` function. Once you've found the component, you can open a connection to it by calling the `OpenComponent` function. You can then use the services of the component by calling its functions.

You can also create your own components and register them with the Component Manager. This allows other applications to use the services of your component.

## The Translation Manager

The Translation Manager is a set of routines that allows you to translate files from one format to another. The Translation Manager is used by Macintosh Easy Open to provide automatic translation of documents.

When the user tries to open a document that your application can't open directly, Macintosh Easy Open will use the Translation Manager to see if it can be translated into a format that your application can open. If it can, the Translation Manager will call the appropriate translation extension to translate the document.

You can also use the Translation Manager to explicitly translate files in your application. To do this, you can use the `TranslateFile` function.

If you want your application to be able to open documents that have been translated by Macintosh Easy Open, you need to add an `'open'` resource to your application. The `'open'` resource tells the Translation Manager which file types your application can open.

## Summary

In this chapter, you've learned how to use the Component Manager and the Translation Manager to extend the capabilities of the Macintosh operating system. You've seen how to find and use components, how to create your own components, and how to use the Translation Manager to translate files from one format to another.

The next chapter describes how to provide online help for users by using the Help Manager.
