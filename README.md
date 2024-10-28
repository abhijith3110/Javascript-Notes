# Javascript-Notes

This file contains important JavaScript concepts with examples, aimed at helping with a deeper understanding of the language.

## Table of Contents
1. [var, let, const](#1-var-let-const)
2. [Hoisting](#2-hoisting)
3. [Data Types](#3-data-types)
4. [Type Casting](#4-type-casting)
5. [Value Comparison](#5-value-comparison)
6. [Loops and Iteration](#6-loops-and-iteration)
7. [This Keyword](#7-this-keyword)
8. [CommonJS and ModuleJS](#8-commonjs-and-modulejs)
9. [Classes](#9-classes)
10. [Closures](#10-closures)
11. [Currying](#11-currying)
12. [Callback Functions](#12-callback-functions)
13. [Promises](#13-promises)
14. [Lexical Scope](#14-lexical-scope)
15. [Array](#15-array)
16. [Higher-Order Functions](#16-higher-order-functions)

---

## 1. var, let, const

In JavaScript, variables can be declared using `var`, `let`, or `const`. Each has different behavior regarding scope, re-declaration, and re-assignment.

### i. var

- **Scope**: Function-scoped.
- **Re-declaration**: Variables declared with `var` can be re-declared.
- **Hoisting**: Variables are hoisted, but initialized with `undefined`.

```javascript
var a = 100; //global

function exampleVar() {
  // console.log(x); // undefined (because of hoisting) (re-declared)
  var x = 10;
  console.log(x); // 10
  if (true) {
    var x = 20; // Same variable, since var is not block-scoped
    console.log(x); // 20
  }
  function sampleVarFn() {
    var x = 30;
    console.log(x); 
    // Inside the sampleVarFn function, a new local variable x is declared with var x = 30; 
    // This variable x is different from the x in the outer exampleVar function because it is in a different scope (the scope of sampleVarFn). 
    // So, inside sampleVarFn, console.log(x) prints 30 and not modified x varibale outside sampleVarFn Function scope.
    console.log(a); //100
  }
  sampleVarFn();
  console.log(a); //100
  console.log(x); // 20 (var is not block-scoped)
}
exampleVar();
```

### ii. let

- **Scope**: Block-scoped.
- **Re-declaration**: Variables declared with `let` can be re-declared but in same scope is not possiable.
- **Hoisting**: Variables are hoisted, but not initialized.
```javascript
function examplelet() {
  // console.log(z); // ReferenceError: z is not defined
  let z = 10;
  console.log(z); //10

  let obj = { name: "John" };
  console.log(obj.name); // john

  if (true) {
    let z = 20; // variable z is declared with the value 20
    console.log(z); // 20
    obj.name = "Jane"; 
    console.log(obj.name); // jane
  }
  console.log(obj.name); //jane
  //obj is still referencing the same object, and since you modified the name property inside the if block, this change persists.
  console.log(z); //10
}

examplelet();

//inside an if block, the object obj is not re-declared. You are only modifying 
//the properties of the same object that exists in memory.

//In short, the object itself is not re-declared, and its properties are mutable, so changes 
//to its properties persist across the whole function scope.

```

### iii. const

- **Scope**: Block-scoped.
- **Re-declaration**: Variables declared with `const` cannot be re-declared.
- **Hoisting**: Variables are hoisted, but not initialized.
- **Mutable reference**: For object and Array, the refrence is constant ,but the value can be still changed.
```javascript
function exampleConst(){
    const z = 10;
    const obj = {
    name:"abhi",
    age:23
}
const arr = [1,2,3,4];

    console.log(z); // 10
    if(true){
        const z = 20;
        console.log(z); // 20
        obj.name = "abhijith";
        console.log(obj); // { name: 'abhijith', age: 23 }
        arr.push(5)
        console.log(arr); // [ 1, 2, 3, 4, 5 ]
    }
    console.log(z); // 10
    console.log(obj);  // { name: 'abhijith', age: 23 }
    console.log(arr); // [ 1, 2, 3, 4, 5 ]
}

exampleConst()
```


