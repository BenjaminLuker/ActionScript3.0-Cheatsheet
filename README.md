# ActionScript 3.0 Cheat Sheet

## What is the ActionScript 3?
ActionScript is an object-oriented programming language derived from HyperTalk and Javascript. ActionScript 3 is the newest version of ActionScript. ActionScript is mostly used for website applications using ActionScript player.

## How to get the ActionScript 3
The most common way to use ActionScript 3.0 is with Adobe Animate. You will have to buy this program from Adobe, but if you want to practice you can get a free trial of the program.

## What ActionScript 3 used for?
ActionScript 3 is used in conjunction with Adobe Flash to create web applications or games. You can find a lot of examples of these types of applications on Newgrounds.com. Most of these games were made in the early 2000s and were pretty popular on the internet, even creating their own subculture on the site.

## A Quick Overview

### Comments
```
// This is a comment
```
```
/* This is a comment that
spans multiple lines */
```

### Variables
Actionscript 3 is a loosely typed language; however, it does requires the *var* statement for any variable declaration.

#### Booleans
```
var myBool:Boolean = true;
```
#### Integers
```
var myInt:int = 10;
```
#### Numbers
```
var myNumber:Number = 10;
```
#### Strings
```
var myString:String = “Hello World”;
```
#### Uints
```
var myUint:uint = 10;
```

### Functions
#### Using a function without parameters
```
Math.random()   // returns a random number from 0 to 1
```
#### Using a function with parameters
```
trace("Hello World")   // prints "Hello World" to the console
```
#### Creating a function
```
var myString:String = "Hello World!"; 
var traceString = function (inputString:String)
{ 
    trace(inputString); 
}; 
traceString(myString);    // prints "Hello World" to the console
```
### Objects and Classes

#### Creating objects
```
var myObject:Object = new Object();
```
```
var myObject:Object = {
  property1:"value1",
  property2:"value2"
}
```
#### Adding and accessing properties
Using either one of the previous examples' objects to add and access a new value
```
myObject.property_name = "newValue";
trace(myObject.property_name);    // prints "newValue"
```
### Operators
#### Additive and multiplicative operators
Takes two operands and performs basic math
```
var myInt:int = 2 + 2;    // returns 4
var myInt:int = 2 - 2;    // returns 0
var myInt:int = 2 * 3;    // returns 6
var myInt:int = 6 / 2;    // returns 3
var myInt:int = 5 % 2;    // returns 1
```
#### Relational and equality operators
Takes two operands, compares them, and returns a boolean
```
if(1<2);    // Less than operator                 returns true
if(1>2);    // Greater than operator              returns false
if(1<=2);   // Less than or equal to operator     returns true
if(1>=2);   // Greater than or equal to operator  returns false
if(1==2);   // Equality operator                  returns false
if(1!=2);   // Inequality operator                returns true
```
#### Logical operators
```
if(1<2 && 2<3)  // AND operator   returns true
if(1<2 || 2>3)  // OR operator    returns true
```
### Arrays
#### Creating arrays
```
var myArray:Array = ["value1", "value2", "value3"];
```
#### Adding values in arrays
Using the previous array
```
myArray.push("data");        // adds "data" as last value in array
myArray.unshift("data");     // adds "data" as first value in array
myArray[2] = "data";         // replaces "data" as 3rd value in array
```
Using the previous array
#### Accessing values in arrays
```
trace(myArray[2]);    // prints "data" to console
```
### Control, Program flow
#### If else statements
```
if(x<10) {
  trace("x is less than ten");
} else if (x > 20) {
  trace("x is greater than twenty");
} else {
  trace("x is between 10 and 20");
}
```
#### For loops
You must initialize a variable before using it in a *for loop*
``` 
var i:int; 
for (i = 0; i < 5; i++) 
{ 
    trace(i);             // prints "0, 1, 2, 3, 4" 
}
```
#### While loops
```
var i:int = 0; 
while (i < 5) 
{ 
    trace(i);             // prints "0, 1, 2, 3, 4" 
    i++; 
}
```
#### Switch statements
```
var myInt:int = 2;
switch(myInt) {
  case 0: 
        trace("myInt = 0"); 
        break; 
    case 1: 
        trace("myInt = 1"); 
        break; 
    case 2: 
        trace("myInt = 2");  
        break; 
    case 3: 
        trace("myInt = 3"); 
        break; 
}
```
## Simple Programs

### Hello World
Use the trace function to print to the output (console)
```
var myString:String = “Hello World”;
trace(myString);
```
### Play and pause buttons
Adobe Animate is a program for creating animations and web applications, and with Actionscript 3 you can interact with them animation through code.  

To get this working, you must first have an animation. Then, create a shape, convert it to a button symbol, and instance the button by going into the properties panel and giving it a name (making sure not to name it *play* or *stop*). For the sake of clarity, I will name my play button *go*. You can double click your button on the canvas to change what it looks like when the button is idle, when you mouse is over it, when you click down onto it, and when you hit it. Once you have done this, create a separate layer for your code, select it, and then you can start working in ActionScript 3.  

The first thing we need to do is stop everything from playing at the beginning.
```
stop();   // this will stop the main timeline from playing
```
If you have movie clips in your animation you will have to stop those each individually.
```
myMovieClip.stop();   // this will stop your movie clip from playing
```
Next, we'll write a function for playing our animation that takes a mouse event and has the return type void.
````
function startPlaying(event:MouseEvent):void {
  play();
}
````
To make our button work, we need to add an EventListener to our button that will execute our function.
```
go.addEventListener(MouseEvent.CLICK, startplaying);
```
In the end, this should be our code:
```
stop();
myMovieClip.stop();

go.addEventListener(MouseEvent.CLICK, startplaying);
function startPlaying(event:MouseEvent):void {
  play();
  myMovieClip.play();
}
```
We can do the same thing to a pause button (which I am calling *halt*).
```
halt.addEventListener(MouseEvent.CLICK, stopplaying);
function stopPlaying(event:MouseEvent):void {
  stop();
  myMovieClip.stop();
}
```
We can also combine the two into one button. In the canvas, double click on the play button, duplicate the frame, and in the second frame swap the symbol for the pause button. Make sure to instance the new pause symbol again. Create a new layer now that we are nested with the two symbols and place your code in their instead of in the main timeline. On the same frame as your play button, place the code for the play button. On the same frame as your pause button, place the code for the pause button. We will now need to modify the code because it is not in the main timeline.

Our play code:
```
stop();
myMovieClip.stop();

go.addEventListener(MouseEvent.CLICK, startplaying);
function startPlaying(event:MouseEvent):void {
  MovieClip(root).play();
  MovieClip(root).myMovieClip.play();
}
```
Our pause code:
```
stop();
myMovieClip.stop();

go.addEventListener(MouseEvent.CLICK, stopplaying);
function stopPlaying(event:MouseEvent):void {
  MovieClip(root).stop();
  MovieClip(root).myMovieClip.stop();
}
```
Finally, we need to switch between the two buttons when we press one.
```
// on our play code
function startPlaying(event:MouseEvent):void {
  MovieClip(root).play();
  MovieClip(root).myMovieClip.play();
  gotoAndStop(2);   // moving to our stop button 
}

// on our pause code
function stopPlaying(event:MouseEvent):void {
  MovieClip(root).stop();
  MovieClip(root).myMovieClip.stop();
  gotoAndStop(1);   // moving to our start button 
}
```
We can now play and pause our animation in our swf file.

## My Thoughts
ActionScript 3 is pretty useful for creating simple games that can run in browser, but in this day and age, there are better way to do this. ActionScript 3 was great when it came out, but frankly, is pretty obsolete now. But there are a few things about the Adobr Animate and ActionScript 3 workflow that I believe other programs should learn from. First of all, I appreciate the way that both animators and programmers use the same interface and tools so that they can work efficiently together. Secondly, I personally like the way that programmers can edit code *in* Adobe Animate without having to do it externally and waiting for the two programs to sync (although that is still an option).
