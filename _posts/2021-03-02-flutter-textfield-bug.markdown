---
layout: post
title:  "Flutter problem when typing in spaces in TextField on ios browser"
date:   2021-03-02 16:11:00 +0100
categories: flutter web 
---
Was encountering a problem trying to spaces into a TextField on flutter web when using an ios mobile browser.
The app  doesn´t respond to pressing the space key in the ios on screen keyboard when viewed on mobile browser
App works fine when viewed on desktop browser. 

Seems to be related to using SingleChildScrollView. Also, seems to depend on which web server is being used.  



Check out the [flutter dartpad gist][flutter-gist]. However. This works, but when installed on our nginx web server the exact same code would not respond to space key presses.

The example works when opened on desktop browser.

[flutter-gist]: https://dartpad.dev/72455ba842e276f147b70451195c52e3
[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/



{% highlight dart %}
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MyHomePage(title: 'Flutter Demo Home Page'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);

  final String title;

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: Center(
        child: SingleChildScrollView(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: <Widget>[
              Text(
                'You have pushed the button this many times:',
              ),
              Text(
                '$_counter',
                style: Theme.of(context).textTheme.headline4,
              ),
              TextField(
                // obscureText: true,
                decoration: InputDecoration(
                  border: OutlineInputBorder(),
                  labelText: 'TextField',
                ),
              ),
            ],
          ),
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: Icon(Icons.add),
      ),
    );
  }
}



{% endhighlight %}

