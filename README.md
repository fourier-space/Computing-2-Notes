# Computing-2-Notes

Javascript files in web apps come in a number of varieties.
Some files are run directly and immediately take actions – these are *main* files;
whilst other files export functionality rather than acting themselves – these are *modules* – and can be imported from main files or other modules.

Javascript files can be made to run in different *runtime environments*, e.g. on a web browser, a web server, or a test suite.
Some javascript files will only make use of the core javascript language features, these are pure javascript files, and can be run in any environment.
Others will make use of features from the interface the environment provides, such as altering the page layout on a web browser, or listening for a request on a web server.
The files that make use of these special features can only be run in the environment they were intended for – you can't run a browser file on the server.

It is important to recognise what kind of file you are looking at, knowing where it will be run, and how it will be called.
Your program might not even run if it tries to call functions from a differnent environment – e.g. there are no html elements on the server, nor functions to access them.
It also helps to structure your programs better if each file has it's own responsibilities.
Your style of coding may also be different depending on the type of file – pure javascript modules may be written in a functional programming style, while the main browser file is likely to be more imperative.

Let's review the types of javascript file you'll work with.

### Main Browser File ###
One of the most important files in a web app is your browser main file.
This is the file that is the entry point to your program on the web browser.
It starts up all the behaviour that you want your web app to have, i.e. constructing the document, setting up event listeners, communicating with a server.

There should be only one main file in each html page, by convention we will call this file `main.js` and we will load it in an html page with the following code:
```html
<script type="module" src="main.js"></script>
```
The main browser file can import any number of pure javascript modules and browser modules.


```bash
node server.js
```

```javascript
import Module from "./module.js";
```

```javascript
const Module = Object.create(null);

Module.property = ...

export default Object.freeze(Module);
```
