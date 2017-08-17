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
- Browser = client, Web Server = server. They talk to each other through HTTP requests
