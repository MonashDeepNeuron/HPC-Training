# Challenges

The challenges for this chapter can found in the [HPC Training Challenges](https://github.com/MonashDeepNeuron/HPC-Training-Challenges) you should have cloned in the previous chapter. Remember to read the README's for each challenge for more details. Your attempts should be added and pushed to this repo in the corresponding directories and files.

> Note:
>
> Do not forget to add a `main()` function which is used to run/test your solutions.

## Overview

- [Challenges](#challenges)
  - [Overview](#overview)
  - [Challenge 1 - Hello World](#challenge-1---hello-world)
  - [Challenge 2 - FizzBuzz](#challenge-2---fizzbuzz)
  - [Challenge 3 - Fibonacci](#challenge-3---fibonacci)
  - [Challenge 4 - GCD \& LCM](#challenge-4---gcd--lcm)
  - [Challenge 5 - Bitwise Add](#challenge-5---bitwise-add)
  - [Challenge 6 - Bitwise Multiply](#challenge-6---bitwise-multiply)
  - [Challenge 7 - Sum and Product Algorithms](#challenge-7---sum-and-product-algorithms)
  - [Challenge 8 - Array Concatenation](#challenge-8---array-concatenation)

## Challenge 1 - Hello World

You're first challenge is to build and run 'Hello World!' on your own device. This should be relatively straight forward as there are no moving parts and the instructions are explicitly given at the start oft he chapter.

## Challenge 2 - FizzBuzz

Create a program called `fizzbuzz.c` that prints the numbers from `0..100` (inclusive) but every number divisible by `3` prints `Fizz` instead and any number divisible by `5` prints `Buzz` and any number divisible by both prints `Fizzbuzz`.

## Challenge 3 - Fibonacci

Create a program called `fib.c` that calculates the first ten fibonacci numbers and prints them to the terminal. The implementation is up to you however, it cannot hard code the values into the program.

## Challenge 4 - GCD & LCM

This challenge consists of two tasks. The first is to create the G.C.D. (Greatest Common Divisor) algorithm. This can be done using whatever techniques you want. The second is to create the L.C.M. (Least Common Multiple) algorithm. This is a bit less common than G.C.D. so you may need to research a bit about it first.

## Challenge 5 - Bitwise Add

For this challenge you have to implement a function called `bitwise_add()` which, given two integers returns their sum using bitwise arithmetic. Any bitwise operators are allowed as well as conditional operators (eg. `==`, `<`). You can use regular arithmetic operators (eg. `+`, `*`) if it is necessary to perform other intermediate calculations but it is possible to solve this challenge without them.

## Challenge 6 - Bitwise Multiply

This challenge is similar to the last but instead of implementing `+` you must implement `*` (product). Your implementation should be contained in a function called `bitwise_multiply()`. You can use any bitwise or conditional operators.

> Note: If you need `+` you can reimplement it internally in `bitwise_multiply` based on your solution from the previous challenge, import it to a header in this challenges folder and include it or copy it to this folder. Ask a trainer if you get stuck with this.

## Challenge 7 - Sum and Product Algorithms

This challenge involves implementing the sum and product reductions on an array or memory block of integers. As a bonus challenge, try and make the algorithms more generic and work with any binary operator.

## Challenge 8 - Array Concatenation

In this challenge you have to implement a general array concatenation function. This should join two arrays of the same type into a single array similar to `strcat()`. As an extra challenge, implement this concatenation algorithm so that if the destination buffer is not large enough, a new buffer of the required size is created and returns the pointer to the new buffer.
