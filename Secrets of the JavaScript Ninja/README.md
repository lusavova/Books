# :muscle: Secrets of the JavaScript ninja - :closed_book: Book Notes

## Understanding the JS language
Compared to other languages like C# or Java, JS is much more *functionally* oriented.
Main differences from other languages include:
- *functions are first - class objects* - functions can be treated like any other JavaScript object
- *function closures* - a function is a closure when it actively maintains ("closes over") the external variables used in its body.
- *prototype-based object orientation* - unlike other programming languages(C#, Java, and Ruby), which use class-based object orientation, JavaScript uses prototypes.

### Lifecycle of a client-side web application:
User enters url or clicks some link, then the browser formulates a request that is sent to a server, which processes the request and formulates a response that is usually composed of HTML, CSS, and JavaScript code. The browser recieve the response and builds a resulting page. Then the user interacts with the page elements and the browser monitors and handle events. Lifecycle ends when the user closes or leaves the web page.

### Page-building phase
Before we can interact with the application, the page must be built from the information in the response received from the server. The goal is to set up the UI of the application.
We have 2 steps:
 - parse the HTML and build the DOM
 - execute the JavaScript code
 
The first step is performed when the browser is processing HTML nodes, and the second step is performed whenever a special type of HTML element - the script element (that contains or refers to JavaScript code) - is encountered. During the page-building phase, the browser can switch between these two steps as many times as necessary.

#### Parsing the HTML and building the DOM
The page-building phase starts with the browser receiving the HTML code. The browser then parse the HTML code, one HTML element at a time, and builds a DOM (a structured representation of the HTML page in which every HTML element is represented as a node).

The head element is used for providing general page information: for example, the page title, character encodings, and external styles and scripts. It isn’t intended for defining page content.

During the construction of the page, the browser can encounter a special type of HTML element, the script element, which is used for including JavaScript code. When this happens, the browser pauses the DOM construction from HTML code and starts executing JavaScript code.

#### Executing JavaScript code
