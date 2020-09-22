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
