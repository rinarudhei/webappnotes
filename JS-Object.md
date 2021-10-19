# **Object**
- an object is a standalone entity, with properties and type
## **"new" syntax**
- It does 5 things:

  - It creates a new object. The type of this object is simply object.
  - It sets this new object's internal, inaccessible, [[prototype]] (i.e. __proto__) property to be the constructor function's external, accessible, prototype object (every function object automatically has a prototype property).
  - It makes the this variable point to the newly created object.
  - It executes the constructor function, using the newly created object whenever this is mentioned.
  - It returns the newly created object, unless the constructor function returns a non-null object reference. In this case, that object reference is returned instead.

## **First-Class Object**

- In javascript functions are first class objects because it can do a lot more than what objects can do.
  - A function is an instance of an Object type. Like an object a function can have properties and can have a link back to it’s constructor function.
```javascript
var o = {}; // empty object 'o'
    o.a = 1 ; 
    o.b = 2 ; 

    console.log(o.a); // 1
    console.log(o.b); // 2 


    function foo(){};
    foo.a = 3 ; 
    foo.b = 4 ; 

    console.log(foo.a);  // logs 3
    console.log(foo.b);  // logs 4 
```
  - Functions can be stored in a variable as a value.
```javascript
var foo = function(){}; 
    console.log(foo); // function(){}
```
  - Functions can be passed as arguments to other functions

```javascript
function callback (foo){
      foo();
}

callback(function(){console.log('Successfuly invoked as an argument inside function callback')})
```
  - You can return a function from a function

```javascript
function foo(){
    return function(){console.log('working!')};
  }

  var bar = foo();
  bar(); // working!
```
  - Can be stored in a variable as a reference.
```javascript
var sum = function (a,b){return a+b}  
    sum(4,4);
```

## **Inheritance**
  - All objects in JavaScript inherit from at least one other object. The object being inherited from is known as the prototype, and the inherited properties can be found in the prototype object of the constructor https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects
  - JavaScript uses prototypal inheritance. This means that, when an object inherits from another, the parent object is known as the child’s prototype.  https://htmldog.com/guides/javascript/advanced/oo/
  - When you ask for a property of an object, JavaScript looks for the property on that object. If it doesn’t find it there, it follows the link to the object’s prototype and looks for the property there. It continues this, up the prototype chain until it finds it, or it returns undefined.

```javascript
// Let's create an object o from function F with its own properties a and b:
let F = function () {
   this.a = 1;
   this.b = 2;
}
let o = new F(); // {a: 1, b: 2}

// add properties in F function's prototype
F.prototype.b = 3;
F.prototype.c = 4;

// do not set the prototype F.prototype = {b:3,c:4}; this will break the prototype chain
// o.[[Prototype]] has properties b and c.
// o.[[Prototype]].[[Prototype]] is Object.prototype.
// Finally, o.[[Prototype]].[[Prototype]].[[Prototype]] is null.
// This is the end of the prototype chain, as null,
// by definition, has no [[Prototype]].
// Thus, the full prototype chain looks like:
// {a: 1, b: 2} ---> {b: 3, c: 4} ---> Object.prototype ---> null

console.log(o.a); // 1
// Is there an 'a' own property on o? Yes, and its value is 1.

console.log(o.b); // 2
// Is there a 'b' own property on o? Yes, and its value is 2.
// The prototype also has a 'b' property, but it's not visited.
// This is called Property Shadowing

console.log(o.c); // 4
// Is there a 'c' own property on o? No, check its prototype.
// Is there a 'c' own property on o.[[Prototype]]? Yes, its value is 4.

console.log(o.d); // undefined
// Is there a 'd' own property on o? No, check its prototype.
// Is there a 'd' own property on o.[[Prototype]]? No, check its prototype.
// o.[[Prototype]].[[Prototype]] is Object.prototype and there is no 'd' property by default, check its prototype.
// o.[[Prototype]].[[Prototype]].[[Prototype]] is null, stop searching,
// no property found, return undefined.
```
- An inherited function acts just as any other property, including **property shadowing** as shown above (in this case, a form of method **overriding**).

## **Object vs Class**
- class itu untuk define property & behaviour dari object. Blueprint for creating objects
