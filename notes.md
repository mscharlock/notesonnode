# Notes on Udemy Course "Understand Node JS"

## V8 Javascript Engine
- Layers of abstraction: Microprocessor + Machine language (ex: ARM, MIPS, x64, etc), Assembly language, C/C++, Javascript (very abstracted)

- Node is written in C++ because V8, the thing that converts JS to MLang is written in C++

## JS Aside: JS Engines and the Ecmascript Specification
- Ecmascript: the standard that JS is based on. Other companies have other engines (besides V8), so we need a standard so the language behaves the same way in all engines
- ECMA International handles the standards
- JS Engine: A program that converts JS into something the computer processor can understand (V8 is an example)

## V8: Under the Hood
- Open Source, from Google, you can actually dl it from github!
- V8 built to be used in Chrome
- .cc / .h are C++ files

## Adding Features to JS
- JS Code > V8 > Machine Code
- OR embed V8 into your own C++ program
- Allows you basically to write something in your C++ that gets converted to MLang and is bound to a JS keyword you define so that allows you to add crazy functionality to JS - neat!
- Node is basically that

## Node Core
- Servers and Clients
- Node.js is a server technology, allows you to write a server in JS
- Client Server Model:
  - A server is a computer performing services, responds to requests from Clients
  - Client asks for services through request
- Browser = client, Web Server = computer connected to the internet. They talk to each other through HTTP requests
- C#, PHP or Ruby are other programming languages for doing stuff with servers
- Node allows us to write JS for servers - wooo

## What does JS need to manage a server?
- Deal with files, databases
- ability to reuse code, ability to accept/send requests
- async
- communicate over the internet

## C++ Core
- Node was developed while this guy was working at Joyent, but available on GH

## JS Core
- process.binding - grabs the C++ and makes it available in the JS

Super random but I want to remember it: 
"Another key concept with classes is "polymorphism", which describes the idea that a general behavior from a parent class can be overridden in a child class to give it more specifics. In fact, relative polymorphism lets us reference the base behavior from the overridden behavior." - [from You Don't Know JS](ttps://github.com/getify/You-Dont-Know-JS/blob/master/this%20%26%20object%20prototypes/ch4.md)

## Events
+ System Events (happen in C++ Core thru libuv?) 
+ Custom Events (happen in JS through the event emitter) 

## JS Aside: 
We can have [] notation or . notation for properties in objects
+ We can also set variable equal to a string value and then use that variable (ex: var prop = 'greet' and then obj[prop] wocould return greet)
We can put functions inside of arrays as items - just the function itself (not the return value) 
+ forEach loops through arrays to invoke all the functions in the array

## Event Emitter: 
emitter.js - we'll write our own emitter
  + could use an ES6 class but here he uses a function constructor
```
function Emitter() {
     this.events = {}; 
}; 

Emitter.prototype.on = function(type, listener) {
     //type is the type of event, listener is the listener listening for the event//
     this.events[type] = this.events[type] || [];
     this.events[type].push(listener); //we're adding functions into the arr//
};
Emitter.prototype.emit = function(type) {
    if (this.events[type]) {
      this.events[type].forEach(function(listener) {
        listener(); 
       });
};
//to emit, we loop through the arr of functions//

module.exports = Emitter;
```
To get the emitter in a different place, we require it in: 
```
var Emitter = require('./emitter'); 
var emtr = new Emitter(); 
emtr.on('greet', function() {
     console.log('Somewhere, someone said hello');
)}; //remember, greet is a property name on an object//
emtr.on('greet', function() {
     console.log('A greeting occured!'); 
}); 

emtr.emit('greet'); //<-- this then makes the two functions we defined above to run on greet to go
```
  














