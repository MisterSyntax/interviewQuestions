/**Q.Explain event delegation.
*A.Allows you to take advantage of event bubbling. Events go down from parent to element, and then bubble back up. This allows you to listen to parent elements for events for child elements. 
**/ 

/**Explain how this works in JavaScript
 * A. this refers to the current object that the called execution function is bound to.
*/
var Obj = {
    a: 1,
    alertA() { 
        alert(this.a);//alerts 1
        alert(this); //alerts the object 
    }
}

/**
 * Explain how prototypal inheritance works
 * if you create an Object of the type of another object var b in the instance below, the prototype of that is the object you passed to create. You can access all its functions and variables. If you call for the prototype of that you'll get the parent type(the object prototype in this case) or null if that prototype is a base element
 * if you use var volvo= new Car(); you can not look at the prototype of Car, instead the proto would give you the obj. 
 */

//each ---> is a call to .__proto__
var a = {a: 1}; 
// a ---> Object.prototype ---> null

var b = Object.create(a);
// b ---> a ---> Object.prototype ---> null
console.log(b.a); // 1 (inherited)

var c = Object.create(b);
// c ---> b ---> a ---> Object.prototype ---> null

var d = Object.create(null);
// d ---> null
console.log(d.hasOwnProperty); 
// undefined, because d doesn't inherit from Object.prototype

//OR
function a(){return 1;}
var b = Object.create(a);

b.__proto__
function a(){return 1;}
b.__proto__.__proto__
//function () {}
b.__proto__.__proto__.__proto__
//Object {}
b.__proto__.__proto__.__proto__.__proto__
//null

/**
 * What do you think of AMD vs CommonJS?
 * CommonJS - use require and export to essentially create objects in js files with functions and values, and access them through other files with require
 * -synchronous
 * AMD - Asynchronous module loading. e.g. require
 */
//CommonJS
    // In circle.js
    const PI = Math.PI;

    exports.area = (r) => PI * r * r;

    exports.circumference = (r) => 2 * PI * r;

    // In some file
    const circle = require('./circle.js');
    console.log( 'The area of a circle of radius 4 is',circle.area(4));

//AMD 
    //Calling define with a dependency array and a factory function
    define(['dep1', 'dep2'], function (dep1, dep2) {

        //Define the module value by returning a value.
        return function () {};
    });

    // Or:
    define(function (require) {
        var dep1 = require('dep1'),
            dep2 = require('dep2');

        return function () {};
    });
/**
 * Explain why the following doesn't work as an IIFE: function foo(){ }();.
 * IIFE (iffy) - Immediately Invoked Function Expression (not declaraton)
 * that's the equivalent of a function declaration followed by another expression; It would throw an error because theres nada in the grouping at the end
 * i.e. functon foo(){}; ();
 */

/**
 * What needs to be changed to properly make it an IIFE?
 * Make it an expression vs a declaration, eg kill foo. Or wrap the whole thing, in a parens and put the executing parens on the outside
 * */
/**
 * What's the difference between a variable that is: null, undefined or undeclared?
 * undeclared - doesn't have var, const, or let. So its in the global space
 * undefined - it hasn't been defined yet 
 * e.g. var obj = {}; obj.a; //returns undefined
 * null - a variable set to a null value
 */

/**
 * How would you go about checking for any of these states?
 * Check to see if === to value, for undeclared, nah thats bad
 */

/**
 * What is a closure, and how/why would you use one?
 * Its used to create scope, to keep private data private, and public access public. Also, to avoid mucking with the global and parent scope.
 * You can create closures by running IIFEs; You can create scope by have a factory function which returns an obj that has accessable methods or values, while keeping other content private
 * Inner functions can access the variables and functions of outer functions, but not the other way around
 **/


/**
 * What's a typical use case for anonymous functions?
 * IIFE, a callback, in a function like map, filter, reduce
 */



/**
 * How do you organize your code? (module pattern, classical inheritance?)
 * Ideally, I'd like to use Asynchronous Module Definition, something like require to manage my modules. I'm a big fan of it for client side js
 * In general, I'm a big fan of modules. I love the idea of creating reusable pieces
 */

/**
 * What's the difference between host objects and native objects?
 * Native Objects - Native to js
 * Host Obj - Something the enviornment(e.g. browser/server) gives you. For example in browser window
 */

/**
 * Difference between: function Person(){}, var person = Person(), and var person = new Person()?
 */
//Function declaration. Gets hoisted
function Person(){}

//functon declaration set to a variable. Does not get hoisted
var person = Person();

//You're setting a variable to the object created by person. It will create a new instance of that person
function Person(param){this.p = param;} } 
var Person = new Person();
//Person variable is a new instance of the Person obj

/**
 * What's the difference between .call and .apply?
 * call takes params 1 at a time
 * apply takes params as an array
 */
//functionToRun.call(ObjectToReference,param1,param2...)
    var myObject;
    function myFunction(a, b) {
        return a * b;
    }
    myObject = myFunction.call(myObject, 10, 2); // returns 20

//this in myFunction
    var myObject = {a:1};
    function myFunction(a, b) {
        this.b = a * b;//this refers to myObject if an object if undefined moves up
        return this;
    }
    myFunction.call(myObject, 10, 2);     
    console.log(myObject);//returns {a:1,b:20}

//.apply
function myFunction(a, b) {
    return a * b;
}
myArray = [10, 2];
myObject = myFunction.apply(myObject, myArray);  // Will  return 20

Explain Function.prototype.bind.
When would you use document.write()?
What's the difference between feature detection, feature inference, and using the UA string?
Explain AJAX in as much detail as possible.
Explain how JSONP works (and how it's not really AJAX).
Have you ever used JavaScript templating?
If so, what libraries have you used?
Explain "hoisting".
Describe event bubbling.
What's the difference between an "attribute" and a "property"?
Why is extending built-in JavaScript objects not a good idea?
Difference between document load event and document ready event?
What is the difference between == and ===?
Explain the same-origin policy with regards to JavaScript.
Make this work:
duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
Why is it called a Ternary expression, what does the word "Ternary" indicate?
What is "use strict";? what are the advantages and disadvantages to using it?
Create a for loop that iterates up to 100 while outputting "fizz" at multiples of 3, "buzz" at multiples of 5 and "fizzbuzz" at multiples of 3 and 5
Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?
Why would you use something like the load event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?
Explain what a single page app is and how to make one SEO-friendly.
What is the extent of your experience with Promises and/or their polyfills?
What are the pros and cons of using Promises instead of callbacks?
What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?
