# FactBurst
A fun and educational app that shares surprising and quirky facts!
import 'package:flutter/material.dart';

void main() {
  runApp(KingpinApp());
}

class KingpinApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Fun Facts About Me',
      home: KingpinHome(),
    );
  }
}

class KingpinHome extends StatefulWidget {
  @override
  _KingpinHomeState createState() => _KingpinHomeState();
}

class _KingpinHomeState extends State<KingpinHome> {
  int _counter = 0;
  String _fact = "Tap the button to reveal a fun fact!";

  final List<String> _facts = [
    "I love to play voilin",
    "I'm a lazy programmer (❁´◡`❁)",
    "I Admired by girls who wear Glasses:)",
    "pyar_dhoka_hai ❤️",
  ];

  void _showNextFact() {
    setState(() {
      _fact = _facts[_counter % _facts.length];
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text("Fun Facts About Me"),
        backgroundColor: Colors.teal,
      ),
      body: Center(
        child: Padding(
          padding: const EdgeInsets.all(16.0),
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              CircleAvatar(
                radius: 60,
                backgroundImage: NetworkImage(
                    'https://i.imgur.com/BoN9kdC.png'), // Example direct image link
              ),
              SizedBox(height: 20),
              Text(
                "Hi, I'm azmeer",
                style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
              ),
              SizedBox(height: 20),
              Text(
                _fact,
                style: TextStyle(fontSize: 18),
                textAlign: TextAlign.center,
              ),
              SizedBox(height: 20),
              ElevatedButton(
                onPressed: _showNextFact,
                child: Text("Show Fun Fact"),
              ),
            ],
          ),
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _showNextFact,
        backgroundColor: Colors.purple,
        child: Icon(Icons.favorite),
      ),
    );
  }
}
