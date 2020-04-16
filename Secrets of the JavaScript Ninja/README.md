# :muscle: Secrets of the JavaScript ninja - :closed_book: Book Notes

## Part 1: Warming up
### Chapter2: Building the page at runtime

Compared to other languages like C# or Java, JS is much more *functionally* oriented.
Main differences from other languages include:
- *functions are first - class objects* - functions can be treated like any other JavaScript object
- *function closures* - a function is a closure when it actively maintains ("closes over") the external variables used in its body.
- *prototype-based object orientation* - unlike other programming languages(C#, Java, and Ruby), which use class-based object orientation, JavaScript uses prototypes.

#### 2.1 Lifecycle of a client-side web application:
User enters url or clicks some link, then the browser formulates a request that is sent to a server, which processes the request and formulates a response that is usually composed of HTML, CSS and JavaScript code. The browser recieve the response and builds a resulting page. Then the user interacts with the page elements and the browser monitors and handle events. Lifecycle ends when the user closes or leaves the web page.

#### 2.2 Page-building phase
Before we can interact with the application, the page must be built from the information in the response received from the server. The goal is to set up the UI of the application.

We have 2 steps:
 - parse the HTML and build the DOM
 - execute the JavaScript code
 
The first step is performed when the browser is processing HTML nodes, and the second step is performed whenever a special type of HTML element - the script element (that contains or refers to JavaScript code) - is encountered. During the page-building phase, the browser can switch between these two steps as many times as necessary.

##### 2.2.1 Parsing the HTML and building the DOM
The page-building phase starts with the browser receiving the HTML code. The browser then parse the HTML code, one HTML element at a time, and builds a DOM (a structured representation of the HTML page in which every HTML element is represented as a node).

The head element is used for providing general page information: for example, the page title, character encodings, and external styles and scripts. It isn’t intended for defining page content.

During the construction of the page, the browser can encounter a special type of HTML element, the script element, which is used for including JavaScript code. When this happens, the browser pauses the DOM construction from HTML code and starts executing JavaScript code.

##### 2.2.2 Executing JavaScript code

All JavaScript code contained in the script element is executed by the browser’s JavaScript engine.

###### - Global objects in JavaScript
The window object object is the global object through which all other global objects, global variables and browser APIs are accessible.

One of the most important properties of the global window object is the document, which represents the DOM of the current page. By using it the JavaScript code can alter the DOM of the page by modifying, removing, creating or inserting elements.

###### - Different types of JavaScript code
Two different types of JavaScript code: **global code** and **function code**

``` javascript
function greet(name){
    return `Hello, ${name}!`;    //Function code is the code contained in a function.
}

var greeting = greet('John');    //Global code is the code outside functions.
console.log(greeting);
```
The main difference between these two types of code is their placement: the code contained in a function is called **function code**, whereas the code placed outside all functions is called **global code**.

These two code types also differ in their execution. Global code is executed automatically by the JavaScript engine line by line, as
it’s encountered. On the other hand, function code, in order to be executed, has to be called by something else: either by global code, by some other function, or by the browser.

JavaScript code can modify the DOM to any degree - it can create new nodes and modify or remove existing DOM nodes, but it can't select and modify elements that haven’t yet been created. This is one of the reasons we put the script elements at the bottom of the page. That way we don’t have to worry if an HTML element has been reached.

Once the JS engine executes the last line of JS code in the script element the browser exits the JS execution mode and continues building DOM nodes by processing the remaining HTML code. If the browser again encounters a script element, the DOM creation from HTML code is again paused and the JS runtime starts executing the contained JS code. 

The global state of the JavaScript application persists in the meantime. All user-defined global variables created during the execution of JavaScript code in one script element are accessible to JavaScript code in other script elements.
(the global window object is alive and accessible during the entire lifecycle of the page)

Both steps: building the DOM and executing the JavaScript code are repeated as long as there are HTML elements to process and JavaScript code to execute. Finally, when the browser runs out of HTML elements to process, the page-building phase is complete and the browser moves on to the event handling.

#### 2.3 Event handling

##### 2.3.1 Event-handling overview
The browser execution environment is based on the idea that *only a single piece of code can be executed at once*: **single-threaded execution model**. Whenever an event occurs, the browser should execute the associated event-handler function. But the user won't wait a lot of time before triggering another event. For this reason, the browser keep track of the events that have occurred but have yet to be processed with an **event queue**.

All generated events are placed in the same event queue, in the order in which they’re detected by the browser. 
First the browser checks the head of the event queue, if there are no events, the browser keeps checking, but if there’s an event at the head of the event queue, the browser takes it and executes the associated handler (if one exists).
The rest of the events wait in the event queue to be processed.

The handling of events, and therefore the invocation of their handling functions, is asynchronous.
Types of events:
- Browser events, such as when a page is finished loading or when it’s to be unloaded
- Network events, such as responses coming from the server (Ajax events, serverside events)
- User events, such as mouse clicks, mouse moves, and key presses
- Timer events, such as when a timeout expires or an interval fires

Before events can be handled, our code has to notify the browser that we’re interested in handling particular events. 

##### 2.3.2 Registering event handlers

## Part 2: Understanding functions
### Chapter 3: First-class functions for the novice: definitions and arguments
### Chapter 4: Functions for the journeyman: understanding function invocation
### Chapter 5: Functions for the master: closures and scopes
### Chapter 6: Functions for the future: generators and promises

## Part 3: Digging into objects and fortifying your code
### Chapter 7: Object orientation with prototypes
### Chapter 8: Controlling access to objects
### Chapter 9: Dealing with collections
### Chapter 10: Wrangling regular expressions
### Chapter 11: Code modularization techniques

## Part 4: Browser reconnaissance
### Chapter 12: Working the DOM
### Chapter 13: Surviving events
### Chapter 14: Developing cross-browser strategies
