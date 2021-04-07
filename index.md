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
- For this tutorial we are going to use _english_words_ package. Import it and add it by following the previous steps.

The following code contains the use of added package.

 ```dart
 import 'package:flutter/material.dart';
 import 'package:english_words/english_words.dart';
 
 void main()=> runApp(MyApp());
 
 class MyApp extends StatelessWidget{
   @overrride
   Widget build(BuildContext context){
   
   final words = WordPair.random(); 
     return MaterialApp(
       theme : ThemeData(primaryColor: Colors.green[400]),
       home: Scaffold(
        appBar: AppBar(title: Text("My First Application")),
        body: Center(child: Text(words.asPascalCase))
       )
     );
   }
 }
 ```
 
 ### Creating a custom widget
 
 ```dart
 import 'package:flutter/material.dart';
 import 'package:english_words/english_words.dart';
 
 class RandomWords extends StatefulWidget{
  @override
  RandomWordsState createState()=> RandomWordsState();
 }
 
 class RandomWordsState extends State<RandomWords>{
  Widget build(BuildContext context){
   return Scaffold(
        appBar: AppBar(title: Text("My First Application")),
        body: Center(child: Text(words.asPascalCase))
       );
  }
 }
 ```
 
 And then integrating it with the prevous code.
 To integrate or use our custom widget we call the class name in the preferred location we want to display the widget. In this case we want to display it inside the body of the scaffold.
 
  ```dart
 import 'package:flutter/material.dart';
 import 'package:english_words/english_words.dart';
 // you need to import the file for the custom widget you created here inorder to use it
 void main()=> runApp(MyApp());
 
 class MyApp extends StatelessWidget{
   @overrride
   Widget build(BuildContext context){
   
   final words = WordPair.random(); 
     return MaterialApp(
       theme : ThemeData(primaryColor: Colors.green[400]),
       home: Scaffold(
        appBar: AppBar(title: Text("My First Application")),
        body: RandomWords()
       )
     );
   }
 }
 ```
## Basic Flutter Widgets

### Text Widget

As the name implies text widget is used to display text on the screen. The text widget is accessible via **Text** constructor. When you provide only a string argument to the widget the color and style will be inherited from the applications theme.
Example: 
```dart
Text("Hello Ambasha");
```
The required parameter for Text widget is a string. To customize the text widget you can use the **TextStyle** class. And google fonts can be used to customize the font. You can also import custom fonts.
Example:
```dart
Text(
  "Hello Ambasha",
  style: GoogleFonts.openSans(
    textStyle: TextStyle(
      color:Colors.green,
      fontSize: 24,

    )
  )
);
```
To add google fonts to your flutter project, you should install **google_fonts** package in pubsec.yams file.

### Row

This widget is used to lineup or display widget in the horizontal axis side by side. By default Row distributes the child widgets over the available space. But you can customize both the space it uses and the alignment of the child widgets.

```dart
Row(
  children: [
    Text("Hello"),
    Text("Ambasha!"),
  ],
),
```

In the default configuration the alignment of the child widget is is at the start or the left edge. But you can customize it by passing different axis alignment.

To place the items at the center:

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.center,
  children: [
    Text("Hello"),
    Text("Ambasha!"),
  ],
),
```
This gathers the child widgets at the center of the Row.

To place the items at the start or the left edge:

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.start,
  children: [
    Text("Hello"),
    Text("Ambasha!"),
  ],
),
```
This gathers the child widgets at the beginning or left edge of the Row.


To place the items at the end or the right edge:

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.end,
  children: [
    Text("Hello"),
    Text("Ambasha!"),
  ],
),
```
This gathers the child widgets at the end or right edge of the Row.


To give equal distance to the child widgets and margin to the child widgets found at the edge:

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.spaceAround,
  children: [
    Text("Hello"),
    Text("Ambasha!"),
  ],
),
```
This adds a an evenly distributed space between the children and gives margin with the same distance from both edges.


To give equal distance to the child widgets and  without a margin to the child widgets found at the edge:

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.spaceBetween,
  children: [
    Text("Hello"),
    Text("Ambasha!"),
  ],
),
```
This adds a an evenly distributed space between the children.

To handle the space covered by the row we use the **mainAxisSize** parameter.
It is used to handle the size of the row and how it utilizes the available space.

- To make the row wrap the children based on the size of the children.
```dart
Row(
  mainAxisSize: MainAxisSize.min,
  children: [
    Text("Hello"),
    Text("Ambasha!"),
  ],
),
```
- To make the row cover the available horizontal space based on the parent widget or maybe a screen size.
```dart
Row(
  mainAxisSize: MainAxisSize.max,
  children: [
    Text("Hello"),
    Text("Ambasha!"),
  ],
),
```

### Column

This widget is used to lineup or display widget in the vertical axis. The column has the same functionality as the row except it does it in an opposite direction. Column tries to cover the available vertical space while a row tries to cover available horizontal space.

```dart
Column(
  children: [
    Text("Hello"),
    Text("Ambasha!"),
  ],
),
```


- To make the column wrap the children based on the size of the children.
```dart
Column(
  mainAxisSize: MainAxisSize.min,
  children: [
    Text("Hello"),
    Text("Ambasha!"),
  ],
),
```
- To make the column cover the available vertical space based on the parent widget or maybe a screen size.
```dart
Column(
  mainAxisSize: MainAxisSize.max,
  children: [
    Text("Hello"),
    Text("Ambasha!"),
  ],
),
```

To place the items at the start or the top edge:

```dart
Column(
  mainAxisAlignment: MainAxisAlignment.start,
  children: [
    Text("Hello"),
    Text("Ambasha!"),
  ],
),
```
This gathers the child widgets at the beginning or top edge of the Column.


To place the items at the end or the bottom edge:

```dart
Column(
  mainAxisAlignment: MainAxisAlignment.end,
  children: [
    Text("Hello"),
    Text("Ambasha!"),
  ],
),
```
This gathers the child widgets at the end or bottom edge of the Column.


To give equal distance to the child widgets and margin to the child widgets found at the edge:

```dart
Column(
  mainAxisAlignment: MainAxisAlignment.spaceAround,
  children: [
    Text("Hello"),
    Text("Ambasha!"),
  ],
),
```
This adds a an evenly distributed space between the children and gives margin with the same distance from both edges.


To give equal distance to the child widgets and  without a margin to the child widgets found at the edge:

```dart
Column(
  mainAxisAlignment: MainAxisAlignment.spaceBetween,
  children: [
    Text("Hello"),
    Text("Ambasha!"),
  ],
),
```
This adds a an evenly distributed space between the children.

**Note:** Both Row and Column don't have a scroll behavior. This means if the size of child widgets is greater than the available space an error will be raised.


### List View

ListView is the most commonly used scrolling widget. It displays its children one after another in the scroll direction. In the cross axis, the children are required to fill the ListView. A list view is like a column having a scroll behavior.
- A list view is used when we are certain that the child widgets my be bigger than the screen size.

```dart
ListView(
  children: [
    Text("Hello"),
    Text("Ambasha!"),
    ],
),
```
The default scrolling direction is the vertical axis. But it can also be changed to the horizontal axis. This can be done by using the **scrollDirection** parameter.

```dart
ListView(
  scrollDirection: Axis.horizontal,
  children: [
    Text("Hello"),
    Text("Ambasha!"),
    ],
),
```

The children of a list view can be added in two ways:
1. By declaring or passing the widgets directly.
    - As seen on the example above.
2. By using list view builder instead.

List view builder is used to create children based on an existing collection. It is recommended to use list view builder rather than filling the children manually.

```dart

final customList = List<int>.generate(100,(i)=>"Item $i");

ListView.builder(
  itemCount: customList.length,
  itemBuilder: (context,index){
    return Text("${customList[index]}");
  }
),
```
### Container

As the name implies containers are used to cover and contain other widgets and customize background color, shape, positioning, sizing, shadow and etc. Over all containers are used to create custom widget shapes or change alignment and rotation.

![container](https://kabjhai.github.io/flutter-crash-course/container.png)

```dart

Container(
  height: 80,
  width: 260,
  color: Colors.blueGrey,
  alignment: Alignment.center,
  transform: Matrix4.rotationZ(-0.25),
  child: Text(
    "Containers!",
    style: TextStyle(
      color: Colors.white,
      fontSize: 25
    )
  )
);
```
- To obtain the rotation we used the **transform** parameter and passed the **Matrix4.rotationZ(-0.25)**. **Matrix4** contains different transformation functions that can be applied to different widgets. **rotationZ(-0.25)** this method specifies the axis of rotation which is Z axis and degree of rotation in which the container is rotated.

To add shadow to the container, give it a border radius or add gradient as a background we change the **decoration** property and use **BoxDecoration** constructor.

**BoxDecoration:**
- The BoxDecoration constructor has multiple properties some of them are:
    - **shape:** This is used to determine the shape of the container. It is default to a rectangle and can be changed to any shape. You have to pass **BoxShape**.
                  For instance, if you want it to be a circle you have to pass **BoxShape.circle**
    - **boxShadow:** This is used to determine the shadow color, spreading radius, blur radius and offset. It accepts a **BoxShadow** as an argument.
    - **gradient:** This is used to determine the mix of colors used to form a gradient, the direction of a gradient and ,where it begins and ends. It accepts a **LinearGradient**,**RadialGradient**,**SweepGradient** as an argument.
    - **LinearGradient:** a progressive transition of two or more colors along a straight line.

```dart
Container(
  child: Center(...),
    width: 100,
    height: 100,
    decoration: BoxDecoration(
      shape: BoxShape.circle,
      boxShadow: [
        BoxShadow(
          color: Colors.grey,
          spreadRadius: 5,
          blurRadius: 7,
          offset: Offset(0, 3),
        ),
      ],
      gradient: LinearGradient(
        begin: Alignment.topCenter,
        end: Alignment.bottomCenter,
        colors: [
            Color(0xffee0000),
            Color(0xffeeee00)
        ],
    )
  ),
);
```

   - **RadialGradient:** a progressive transition of two or more colors radiating around a central.

```dart
Container(
  child: Center(...),
    width: 100,
    height: 100,
    decoration: BoxDecoration(
      shape: BoxShape.circle,
      boxShadow: [
        BoxShadow(
          color: Colors.grey,
          spreadRadius: 5,
          blurRadius: 7,
          offset: Offset(0, 3),
        ),
      ],
      gradient: RadialGradient(
    center: Alignment(0.7, -0.6), // near the top right
    radius: 0.2,
    colors: [
      Color(0xFFFFFF00), // yellow sun
      Color(0xFF0099FF), // blue sky
    ],
    stops: [0.4, 1.0],
  )
  ),
);
```

   - **SweepGradient:** a progressive transition of two or more colors with a circular sweep on a central point.


```dart
Container(
  child: Center(...),
    width: 100,
    height: 100,
    decoration: BoxDecoration(
      shape: BoxShape.circle,
      boxShadow: [
        BoxShadow(
          color: Colors.grey,
          spreadRadius: 5,
          blurRadius: 7,
          offset: Offset(0, 3),
        ),
      ],
      gradient: SweepGradient(
      center: FractionalOffset.center,
      startAngle: 0.0,
      endAngle: math.pi * 2,
      colors: <Color>[
        Color(0xFF4285F4), // blue
        Color(0xFF34A853), // green
        Color(0xFFFBBC05), // yellow
        Color(0xFFEA4335), // red
        Color(0xFF4285F4), // blue again to seamlessly transition to the start
      ],
      stops: <double>[0.0, 0.25, 0.5, 0.75, 1.0],
    ),
  ),
);
```

### Stack and Positioned

If you want to overlap widgets or freely position your widgets at your desired position you can use **Stack** and **Positioned** widgets respectively.
Since, a stack doesn't constrain size if the widgets are out of the screens bound an overflow error will not appear.

```dart
Stack(
  children: [
    Container(
      width: 40,
      height: 40,
      decoration:  BoxDecoration(
        color: Colors.red
      )
    ),
     Text("Hello Ambasha!"),
  ]
)
```
The code above will overlap the text widget and the container. Wich makes the container the background to the text. 
**Note:** The order in which items are stacked depends on the order in which they are added. The children placed at the bottom are the once to be on top. Assuming that the order in which the items are added in the list from top to bottom the stack widget has the same property with stack datastructure.

If you want to move the children to your desired position you have to use **Positioned** widget.
Positioned constructor has top and left parameters. The top parameter is used to add margin to the item from the top available position on the screen. And left gives margin to the widget from the left. Giving it negative margin from the top or left moves the widget out of the screen.
```dart
Stack(
  children: [
    Positioned(
      top: 30,
      left: 75
      child: Text("Hello Ambaashaa"),
    )
  ]
)
```

### When should I use stateless and statefull widget?

- If you have variables which have to be declared final or constant and the UI doesn't have to change when the value of a variable changes **Stateless Widgets** should be used.
```dart
class MyName extends StatelessWidget {
final String name;
MyName(this.name);
  @override
  Widget build(BuildContext context){
    return Text(name);
  }
}
```
In the example above the value of the variable name doesn't change. For that reason a final variable is used and since the value of the class can't be changed the constructor is also declared constant.

- If the state of the user interface depends on the values of a variable or a value fetched from a remote source a **Statefull Widget** should be used.
      - When you create a statefull widget a create state method should be called and it should construct the state class. And the state class should be *package private*.
      
       ```dart
       class Counter extends StatefulWidget {
          Counter();
          @override
          _CounterState createState() => _CounterState();
      }
      ```
- When you have a variable that can affect the user interface or the user interface has to change with, it should not be final or constant.
- The state variables should be initialized and it is recommended if the variables are package private.
- **setState()** method is used to make the change to the state and for the UI to be rebuilt without affecting the satate.

       ```dart
       class Counter extends StatefulWidget {
          Counter();
          @override
          _CounterState createState() => _CounterState();
      }

      class _CounterState extends State<Counter> {
        int _counter = 0;
        @override
        Widget build(BuildContext context) {
          return Column(
            children: [
              Text("$_counter"),
              IconButton(
                child: Icon(Icons.add),
                onPressed: () {
                  setState(() => _counter++);
                }
              ),
            ],
          );
        }
      }
      ```
## Building UIs in Flutter

Even though flutter gives you the opportunity to design widgets from scratch it also gives you pre-built widgets that you can use to build a user interface.
There are two predifined design UIs in flutter:

  1. Material design
  2. Cupertino design 

### Material Design

Flutter gives you a series of pre-built components to create apps embracing the typical Android design, also known as **Material Design**.
There are two ways to create material layouts:
1. Building the layout from scratch
2. Importing the **material.dart** package

### Scaffold

As seen on the previous section scaffold gives a material layout with multiple widgets support.
Some of the widgets that can be integrated in scaffold are:
1. App Bar
2. Drawer
3. Floating Action Button


### App Bar

An AppBar is the equivalent of **Toolbar** class in Java/Kotlin. It is always displayed at the top of the screen. The AppBar is where menu's, drawers and icon buttons can be added to fulfill different requirements or the application.

Main components of an AppBar are Drawer Button, App title, Action buttons, back button to return to previous page.

![app bar](https://kabjhai.github.io/flutter-crash-course/appBar.png)

- If we have multiple views when developing an application the users should have the option to return to the previous view or page. To give that option to the user the value of **automaticallyImplyLeading** inside an app bar constructor should be set to **true**.

```dart
Scaffold(
        appBar: AppBar(
          automaticallyImplyLeading: true,
          title: Text("My First Application"),
        ),
)
```

- To add additional buttons on the app bar for displaying menu or doing a predifined action the value of **actions** should be filled with list of widgets *(It is preferred if Icon Buttons are passed in the actions argument)*. 

- **IconButton:** Icon Buttons are material widgets that display icon to identify the button. Icon buttons contain **icon** and **onPressed** as arguments to accept the Icon to display and the action to take or perform when the button is clicked.

```dart
Scaffold(
        appBar: AppBar(
          automaticallyImplyLeading: true,
          title: Text("My First Application"),
          actions:[
            IconButton(
              icon: Icon(Icons.info),
              onPressed: (){
                print("Info button pressed")
              }
            )
          ]
        ),
)
```

### Drawer 

A drawer is a container that horizontally slides from a side of the screen to show a series of items. When a drawer is added to a Scaffold a menu icon is automatically added to the appBar to open the drawer.

In scaffold there are two arguments that can be used to add a drawer.
1. drawer : This makes the drawer open from left to right.
2. endDrawer : This makes the drawer open from right to left.

- Both of the arguments accept a widget as a parameter. We can create a drawer by using a Drawer constructor or any other container widgets that we can add child to. For this section we will use a drawer constructor to create a drawer.

- A drawer has a child argument that accepts widgets.

```dart
Scaffold(
    drawer: Drawer(
    child: ListView(
        Text("Item 1"),
        Text("Item 2"),
        Text("Item 3"),
        Text("Item 4"),
      )
    ),
)
```

- To display icons side by side with texts we can use a widget called **ListTile**.
- **ListTile** constructor takes three arguments:
      - leading: This takes an icon as a value and displays the icon at the left side
      - title: This takes a text and used to display the text explaining the menu
      - onTap:  This is where we write the code to define what happens when the user clicks on it


```dart
Scaffold(
    drawer: Drawer(
    child: ListView(
        ListTile(
        leading: Icon(Icons.people),
        title: Text("Item 1"),
        onTap: () {},
        )  
        ListTile(
        leading: Icon(Icons.people),
        title: Text("Item 2"),
        onTap: () {},
        )
        ListTile(
        leading: Icon(Icons.people),
        title: Text("Item 3"),
        onTap: () {},
        )
      )
    ),
)
```

- To change the direction in which the drawer opens use **endDrawer** instead of **drawer**.

### Floating Action Button

Also known as **FAB**, it is a special rounded button with elevation that usually appears on the bottom-right corner of the screen. 
To add a floatingActionButton to a scaffold you have to pass **FloatingActionButton** constructor to the **floatingActionButton** argument.

- FloatingActionButton takes three major arguments 
    - **child:** takes an icon widget as an argument,
    - **backgroundColor:** takes color as an argument,
    - **onPressed:**  Takes what to do when the button is clicked.


```dart
Scaffold(
    floatingActionButton: FloatingActionButton(
      child: Icon(Icons.add),
      backgroundColor: Colors.red,
      onPressed: () {
        print("FAB Pressed");
      },
    ),
)
```

- You can change the location of the FAB by passing **FloatingActionButtonLocation** value to **floatingActionButtonLocation** argument in the scaffold.


```dart
Scaffold(
    floatingActionButton: FloatingActionButton(
      child: Icon(Icons.add),
      backgroundColor: Colors.red,
      onPressed: () {
        print("FAB Pressed");
      },
    ),
    floatingActionButtonLocation: FloatingActionButtonLocation.centerFloat,
)
```
### Buttons

Buttons are widgets that are used to execute an action when a click event or tap event occurs.
Flutter has four types of buttons predifined and a customizable Material and Image buttons. 
The most commonly used buttons are:
1. Raised Button : a rectangular android button with a default elevation and shadow. 
  ![raisedButton](https://kabjhai.github.io/flutter-crash-course/raisedButton.png)
2. Flat Button : the same are raised button with no elevation and shadow.
  ![flatButton](https://kabjhai.github.io/flutter-crash-course/flatButton.png)
3. Button Bar : it is a horizontal container of buttons to display multiple options to choose from. It has the same property as the **Row** widget.
  ![buttonBar](https://kabjhai.github.io/flutter-crash-course/buttonBar.png)
4. Icon Button : it is a button with an icon rather than a string.
  ![buttonBar](https://kabjhai.github.io/flutter-crash-course/buttonBar.png)
5. Image Button :  it is a button with an image rather than a string.

```dart
  ButtonBar(
    alignment: MainAxisAlignment.center,
    children: [
      FlatButton(
        onPressed: () {},
        child: Text("No")
      ),
      RaisedButton(
        onPressed: () {},
        child: Text("YES")
      ),
    ],
  );
```