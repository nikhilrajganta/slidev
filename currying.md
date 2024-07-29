---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true
---

# Functional Programming Concepts

---

## Currying

<v-clicks>

Currying is a technique where a function that takes multiple arguments is transformed into a sequence of functions, each taking a single argument. It allows you to create specialized versions of a function by partially applying some of its arguments.

### Example:

```javascript
// Non-curried function
function add(a, b) {
  return a + b;
}

// Curried function
function addCurried(a) {
  return function (b) {
    return a + b;
  };
}

const add5 = addCurried(5);
console.log(add5(3)); // Output: 8
console.log(add5(10)); // Output: 15
```

</v-clicks>

---

## Partial Application

Partial application is the process of creating a new function by pre-filling some of the arguments of an existing function. It's similar to currying, but the resulting function can take more than one argument.

### Example:

```javascript
// Non-partially applied function
function multiply(a, b) {
  return a * b;
}

// Partially applied function
function multiplyBy5(b) {
  return multiply(5, b);
}

console.log(multiplyBy5(3)); // Output: 15
console.log(multiplyBy5(10)); // Output: 50
```

---

## Point-free Code

Point-free, also known as tacit programming, is a style of programming where function definitions do not explicitly mention the function's arguments. This is achieved by using higher-order functions (functions that take other functions as arguments or return functions) to compose simpler functions.

### Example:

```javascript
// Non-point-free
function addOne(x) {
  return x + 1;
}

// Point-free
const addOne = (x) => x + 1;
```

Real-world example:
In a functional programming library like Lodash or Ramda, you might use point-free style to create composable, reusable functions. For example, you could create a function that filters an array, maps the results, and then sums the values:
javascript  
// Point-free style
const sumOfDoubledPositives = compose(
sum,
map(double),
filter(isPositive)
);
