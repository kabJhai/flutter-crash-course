## Flutter Crash Course

### What's flutter?

It is a Google UI development framework for building natively compiled applications for all devices.
It is cross platform and extremely fast compared to other frameworks. It doesn't require a javascript brigdge and it uses the native ARM.

**ARM**: This is a mobile processor architecture first and foremost, and what the majority of phones run now. Qualcomm's Snapdragon, Samsung's Exynos, and MediaTek's mobile chips are all examples of ARM processors.


Flutter uses a programming language called dart. It is an object oriented language and it can run on almost every platforms. The language structure is similar to JavaScript and Java

Everything in flutter is a widget. And since flutter follows material design the name of the widgets is the same as the names used in material design for different widgets.
- Scaffold
- AbbBar
- Container
- Image
- Icon
- ImageButton
- RaisedButton and etc

Every widget has a high level and low level widget nested inside of it to build the UI.
Widgets are classified into two
1. Stateless
2. Stateful

And every widget is built to be passed and displayed or used inside flutter.

### Stateless Widgets
Stateless widgets are immutable and their states can not change during the runtime of the application.
**Example:**

```dart
import 'package:flutter/material.dart';
class HomePage extends StatelessWidget {
 @override
 Widget build(BuildContext context){
    return Container();
 }
}
```

### Stateful Widgets

Stateful widgets are mutable and their states can change during runtime of the program. This means the widget is redrawn based on the state changes.
**Example:**

```dart
import 'package:flutter/material.dart';
class HomePage extends StatefulWidget {
 @override
 _HomePageState createState()=> _HomePageState();
}

class  _HomePageState extends State<HomePage> {
 @override
 Widget build(BuildContext context){
   return Container();
 }
}
```

### Development Environment

For users using Windows
- Android Studio
- Android SDK
- Android Emulator or Phone
- Flutter Plugin for Android Studio
- Visual Studio Code and flutter extension [To use VSCode]

For Mac users
- XCode
- IOS Simulator

To setup your development environment and download flutter SDK click [here](https://flutter.dev/docs/get-started/install)


### Create a flutter app

- To create a flutter app open _cmd_ or _terminal_ and type `flutter create applicationName`. 
- Then type `cd applicationName`
_applicationName_ is just a template name for you to replace with your preferred application name.
- Then you can open it with your prefered IDE (Android Studio / VSCode).
- To open it with VSCode type `code .` in your project directory terminal.


### Flutter Boilder Plate Description

 After your code is generated you will see multiple folders created by flutter.
 - **android** folder: This folder contains the native files for android and you can add custom codes to add additional support for libraries or configure the manifest file or other native android configurations.
 - **ios** folder:  It has the same purpose as android folder.
 - **build** folder: It contains build codes during debuging and final release of the application.
 - **lib** folder: It is where you write your dart code.
 - **pubsec.yaml** file: It contains all the important information about your application including packages, assets application name or build number, package configuration and etc.
 
 
 The code below creates a material application that has an app bar with title 'My First Application' and A body 'Hello Meh!'.
 
 ```dart
 import 'package:flutter/material.dart'
 
 void main()=> runApp(MyApp());
 
 class MyApp extends StatelessWidget{
   @overrride
   Widget build(BuildContext context){
     return MaterialApp(
       theme : ThemeData(primaryColor: Colors.green[400]),
       home: Scaffold(
        appBar: AppBar(title: Text("My First Application")),
        body: Center(child: Text("Hello Meh!"))
       )
     );
   }
 }
 ```


### What is Material App?

An application that uses material design.

A convenience widget that wraps a number of widgets that are commonly required for material design applications. It builds upon a WidgetsApp by adding material-design specific functionality, such as AnimatedTheme and GridPaper.

The MaterialApp configures the top-level Navigator to search for routes in the following order:

For the / route, the home property, if non-null, is used.

Otherwise, the routes table is used, if it has an entry for the route.

### What is a Scaffold?

Implements the basic material design visual layout structure.

This class provides APIs for showing drawers and bottom sheets.

To display a persistent bottom sheet, obtain the ScaffoldState for the current BuildContext via Scaffold.of and use the ScaffoldState.showBottomSheet function.


### What is theme data?

Defines the configuration of the overall visual Theme for a MaterialApp or a widget subtree within the app.

The MaterialApp theme property can be used to configure the appearance of the entire app. Widget subtree's within an app can override the app's theme by including a Theme widget at the top of the subtree.

Widgets whose appearance should align with the overall theme can obtain the current theme's configuration with Theme.of. Material components typically depend exclusively on the colorScheme and textTheme. These properties are guaranteed to have non-null values.



### Adding Packages

To add flutter packages:
- You need to go to **pub.dev** and search for the required package.
add it under dependencies: in the **pubsec.yaml** file.

- Open the terminal and type `flutter pub get`
- Then import the package into the file.

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```
