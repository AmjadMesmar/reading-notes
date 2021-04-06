# Functional Programming Concepts

![SQL](../201classes/Images201/js.png)

## What is functional programming?

- Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.

## Pure functions

The first fundamental concept we learn when we want to understand functional programming is pure functions. But what does that really mean? What makes a function pure?

So how do we know if a function is pure or not? Here is a very strict definition of purity:

1. It returns the same result if given the same arguments (it is also referred as ***deterministic***).
2. It does not cause any observable side effects.

It returns the same result if given the same arguments

Imagine we want to implement a function that calculates the area of a circle. An impure function would receive radius as the parameter, and then calculate ***radius * radius * PI***:

        let PI = 3.14;

        const calculateArea = (radius) => radius * radius * PI;

        calculateArea(10); // returns 314.0

- Why is this an impure function? Simply because it uses a global object that was not passed as a parameter to the function.

Now imagine some mathematicians argue that the PI value is actually 42and change the value of the global object.

Our impure function will now result in 10 * 10 * 42 = 4200. For the same parameter (radius = 10), we have a different result. Let's fix it!

        let PI = 3.14;

        const calculateArea = (radius, pi) => radius * radius * pi;

        calculateArea(10, PI); // returns 314.0

Now we’ll always pass thePI value as a parameter to the function. So now we are just accessing parameters passed to the function. **No external object**.

1. For the parameters radius = 10 & PI = 3.14, we will always have the same the result: 314.0
2. For the parameters radius = 10 & PI = 42, we will always have the same the result: 4200

## Pure functions benefits

The code’s definitely easier to test. We don’t need to mock anything. So we can unit test pure functions with different contexts:

1. Given a parameter A → expect the function to return value B.
2. Given a parameter C → expect the function to return value D.

A simple example would be a function to receive a collection of numbers and expect it to increment each element of this collection.

        let list = [1, 2, 3, 4, 5];

        const incrementNumbers = (list) => list.map(number => number + 1);

We receive the numbers array, use map incrementing each number, and return a new list of incremented numbers.

        incrementNumbers(list); // [2, 3, 4, 5, 6]

For the input [1, 2, 3, 4, 5], the expected output would be [2, 3, 4, 5, 6].

## Filter

Given a collection, we want to filter by an attribute. The filter function expects a true or false value to determine if the element should or should not be included in the result collection. Basically, if the callback expression is true, the filter function will include the element in the result collection. Otherwise, it will not.

A simple example is when we have a collection of integers and we want only the even numbers.

Imperative approach

An imperative way to do it with Javascript is to:

1. create an empty array evenNumbers
2. iterate over the numbers array
3. push the even numbers to the evenNumbers array

        var numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
        var evenNumbers = [];

        for (var i = 0; i < numbers.length; i++) {
          if (numbers[i] % 2 == 0) {
            evenNumbers.push(numbers[i]);
          }
        }

- We can also use the ***filter*** higher order function to receive the even function, and return a list of even numbers:

**References:**

- Concepts of Functional Programming in Javascript [Read the full article here](https://medium.com/the-renaissance-developer/concepts-of-functional-programming-in-javascript-6bc84220d2aa)

- Refactoring JavaScript for Performance and Readability (with Examples!)  [Read the full article here](https://dev.to/healeycodes/refactoring-javascript-for-performance-and-readability-with-examples-1hec/)

## [Main page](https://amjadmesmar.github.io/reading-notes/)