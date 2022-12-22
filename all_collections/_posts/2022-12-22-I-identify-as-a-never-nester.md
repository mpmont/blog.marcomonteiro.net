---
layout: post
title: I identify as a never nester
date: 2022-12-22
tag: linux, webdev, php, sublime, standards
description: How to better structure your code with less nesting
author: Marco Monteiro
categories: [ linux, webdev, php, sublime, standards ]
---
It is not uncommon for programmers to use indentation to organize and structure their code. This practice, known as "nesting," helps to visually group related code blocks and make the overall structure of the code more clear and easy to understand. However I've started to addopt something called never nesting. So what is never nesting?

<!--more-->

Here's an example of some PHP code with some levels of nesting in it. To be precise it has 4 levels of nesting.

    function calculateSum($numbers) {
      $sum = 0;
      if (is_array($numbers)) {
        foreach ($numbers as $number) {
          if (is_numeric($number)) {
            $sum += $number;
          } else {
            throw new Exception("Error: Non-numeric value found in array.");
          }
        }
      } else {
        throw new Exception("Error: Input is not an array.");
      }
      return $sum;
    }

This function takes an array of numbers as input and calculates the sum of all the numeric values in the array. It has three levels of nesting:

1 The outermost level is the calculateSum function itself.

2 The second level is the if statement that checks whether the input is an array.

3 The third level is the foreach loop that iterates over each element in the array.

4 The fourth level is the if statement inside the loop that checks whether each element is a numeric value.

Each level of nesting is indented to make the structure of the code more clear and easy to follow. **Or is it?**

Basically with a **never nesting** concept everything that goes beond 3 levels should not exist. We basically have two ways of achieving this, we can use **Extraction** or **Inversion**.

# Extraction method

With the extraction method basically we should create new functions to remove some the nesting. So with the same code we can do the following.


    function calculateSum($numbers) {
      $sum = 0;
      if (is_array($numbers)) {
        foreach ($numbers as $number) {
          $sum += isValidNumberSum($number);
        }
      } else {
        throw new Exception("Error: Input is not an array.");
      }
      return $sum;
    }

    function isValidNumberSum($input) {
      if (is_numeric($input)) {
        return $input;
      } else {
        throw new Exception("Error: Non-numeric value found in array.");
      }
    }


The isValidNumber function is a now a new function that encapsulates the is_numeric check. It returns true if the input is a numeric value, and throws an exception if it is not.

You now have an extra function that can be used in other contexts and better yet, your initial function only goes 3 levels deep nesting.

# Inversion

To rewrite the calculateSum function using an "inversion of control" concept, where it focuses on failure cases first and then the actual use of the function, we can use the following approach:

    function calculateSum($numbers) {
      if (!is_array($numbers)) {
        throw new Exception("Error: Input is not an array.");
      }
      $sum = 0;
      foreach ($numbers as $number) {
        if (!is_numeric($number)) {
          throw new Exception("Error: Non-numeric value found in array.");
        }
        $sum += $number;
      }
      return $sum;
    }

n this version of the function, the first thing we do is check whether the input is an array. If it is not, we throw an exception. This is an example of "failing fast," as we are immediately handling and reporting an error condition rather than continuing to process the input.

Then, we iterate over each element in the array and check whether it is a numeric value. If it is not, we again throw an exception.

Finally, if all of the input values are valid, we calculate and return the sum of the numeric values in the array.

This approach allows us to handle and report errors as soon as they are detected, rather than waiting until the end of the function to check for errors. This can make the code more robust and easier to maintain, as it is clearer which conditions can cause the function to fail and how to handle those failures.

# Combine both Inversion and Extraction

The best way of doing things is to combine both. And in this case you'll end up with something like this:


    function calculateSum($numbers) {
      if (!is_array($numbers)) {
        throw new Exception("Error: Input is not an array.");
      }
      $sum = 0;
      foreach ($numbers as $number) {
        foreach ($numbers as $number) {
          $sum += isValidNumberSum($number);
        }
      }
      return $sum;
    }

    function isValidNumberSum($input) {
      if (is_numeric($input)) {
        return $input;
      }
      throw new Exception("Error: Non-numeric value found in array.");
    }

In this case we even went a step further and removed the else statement in our isValidNumberSum function, since we know if the number is not returned you can assume its not a number and just throw a new exception.

I've been adapting all my code to this approach and its way more redable because I know the start of any function is focussed on the errors and exceptions and the actual code will be in the end.