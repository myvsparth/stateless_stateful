# Stateful and Stateless Widget Flutter Example
## Description

Basic understanding of flutter stateless and stateful widget. Where and in which scenario to use and how to use.

## Introduction

Flutter is all about collection of widgets. Like if you have familiar with other programming languages like react native, android, or ionic.
Flutter Widget = React Native Components = Ionic Components/Controllers = Android Activities. Everything you made is widget in short.
Button, Tabs, ListView, Drawer, Gridview etc all are the widgets.

#In short Understanding:
Stateless widgets are those when you want to make a UI which do not need to be dynamically changed when you update any value bound to it.
For Eg. You want to make a button whose title need not changed dynamically then you can create a separate widget for button as stateless widget.

Stateful widgets is just vice versa to stateless widget means when you want to make something that you want to change dynamically according to user interacts with it then you can use stateful widget.
For Eg. you want to change the background color of app on click of button then you can make use stateful widget in this case.

Stateful widget can contain another stateless widget and vice versa.

#Example
The idea is to create a simple app in which background color will be changed(toggle) when we click on the button.

Steps:

1. Create new flutter app and remove everything in main.dart file.

2. Import the material package. Material package contains all the readymade widgets of the google material design concept.
	
        import 'package:flutter/material.dart';

3. Define main method of the app which is the entry point of the app.
	
        void main() => runApp(MyApp());

4. Defining Stateless Widget which include UI that will not changed dynamically.

        class MyApp extends StatelessWidget {
        @override // StatelessWidget must override build()
        Widget build(BuildContext context) {
        return MaterialApp(
            title: 'Stateless & Stateful',
            theme: ThemeData(
            primarySwatch: Colors.blue,
            ),
            home: Scaffold(
            appBar: AppBar(
                title: Text('Stateless & Stateful'),
            ),
            body: BackgroundPage(), // including stateful widget in stateless widget
            ),
        ); 
        }

5. Defining Stateful Widget which include UI that will change dynamically.

        class BackgroundPage extends StatefulWidget {
        // stateful widget
        @override
        _BackgroundPageState createState() => _BackgroundPageState();
        }

        class _BackgroundPageState extends State<BackgroundPage> {
        // State<BackgroundPage> created class with state which extends state of type BackgroundPage
        Color backgroundColor = Colors.green;
        @override
        Widget build(BuildContext context) {
        return Container(
            decoration: BoxDecoration(color: backgroundColor),
            height: MediaQuery.of(context).size.height,
            width: MediaQuery.of(context).size.width,
            child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: <Widget>[
                RaisedButton(
                child: Text('Change Color'),
                onPressed: () {
                    setState(() { // any state change must be included between setState() otherwise state value changed but not reflect in UI. each time setState() called build() method called again but only changes the UI which would be required for state value changes. like in our example it regenerates only background color nothing else.
                    if (backgroundColor == Colors.green)
                        backgroundColor = Colors.red;
                    else
                        backgroundColor = Colors.green;
                    });
                },
                
            ],
            ),
        ); 
        }

6. Run the app in emulator/simulator or in real device.
7. After running the app you can see that  on clicking in “Change Color” button the background toggled from red to green and vice versa.


For help getting started with Flutter, view our 
[online documentation](https://flutter.dev/docs), which offers tutorials, 
samples, guidance on mobile development, and a full API reference.

