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
console.log(x); // undefined (hoisted but not initialized)
var x = 5;
console.log(x); // 5

// Redeclaration
var x = 10;
console.log(x); // 10

