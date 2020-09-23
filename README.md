# Statemanagement-with-Provider
In this tutorial, we teach you how to use Provider package for state management.
## What is Provider
Provider is a package that contains useful state management functionality, and it's currently recommended for beginners.

For the sake of simplicity and utilization of official Flutter documentation. We will refer to the app created by the Flutter Dev team, but we will explain it in a more, lazy way.


![Image of Yaktocat](https://flutter.dev/assets/development/data-and-backend/state-mgmt/model-shopper-screencast-e0ada0e83cd8e7fdcad84167b8f7ffd7eb5ef85b0cb8957f03c6f05bd16b1cea.gif)

For illustration, consider the following simple app.

The app has two separate screens: a catalog, and a cart (represented by the MyCatalog, and MyCart widgets, respectively). It could be a shopping app, but you can imagine the same structure in a simple social networking app (replace catalog for “wall” and cart for “favorites”).

The catalog screen includes a custom app bar (MyAppBar) and a scrolling view of many list items (MyListItems).

Here’s the app visualized as a widget tree.


![Image of Yaktocat](https://flutter.dev/assets/development/data-and-backend/state-mgmt/simple-widget-tree-8fe7a45d88d5007510b3f2f27caa845a0453663d4e5c60b5c8d0dc036ad8a966.png)

With provider, you don’t need to worry about callbacks or InheritedWidgets. But you do need to understand 3 concepts:

1. ChangeNotifier
2. ChangeNotifierProvider
3. Consumer

## ChangeNotifier

ChangeNotifier is a simple class included in the Flutter SDK which provides change notification to its listeners. In other words, if something is a ChangeNotifier, you can subscribe to its changes. 

The only code that is specific to ChangeNotifier is the call to notifyListeners(). Call this method any time the model changes in a way that might change your app’s UI.

## ChangeNotifierProvider

ChangeNotifierProvider is the widget that provides an instance of a ChangeNotifier to its descendants. It comes from the provider package.

We already know where to put ChangeNotifierProvider: above the widgets that need to access it. 
You don’t want to place ChangeNotifierProvider higher than necessary (because you don’t want to pollute the scope).

## Consumer

The only required argument of the Consumer widget is the builder. Builder is a function that is called whenever the ChangeNotifier changes. (In other words, when you call notifyListeners() in your model, all the builder methods of all the corresponding Consumer widgets are called.

The builder is called with three arguments. The first one is context, which you also get in every build method.

The second argument of the builder function is the instance of the ChangeNotifier. It’s what we were asking for in the first place. You can use the data in the model to define what the UI should look like at any given point.

The third argument is child, which is there for optimization. If you have a large widget subtree under your Consumer that doesn’t change when the model changes, you can construct it once and get it through the builder.

> It is best practice to put your Consumer widgets as deep in the tree as possible. You don’t want to rebuild large portions of the UI just because some detail somewhere changed.
