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
