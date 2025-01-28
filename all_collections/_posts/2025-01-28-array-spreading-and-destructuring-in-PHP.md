---
layout: post
title: Array spreading and destructuring in PHP
date: 2025-01-28
tag: webdev, php, modern-php
description: How to properly use array spreading and destructuring in PHP.
author: Marco Monteiro
categories: [php, modern-php]
---
PHP 7.4 introduced array spreading and destructuring, powerful features that simplify how we work with arrays. Let's explore how to use these modern PHP features to write cleaner, more maintainable code.

<!--more-->

This is a simple example on how people tend to use arrays in their projects.

    $person = [
        'name' => 'John Doe',
        'age' => 30,
        'email' => 'john.doe@example.com',
    ];

    $name = $person['name'];
    $age = $person['age'];
    $email = $person['email'];

This works, but it's not the best way to do it. We can use array spreading and destructuring to make this code more readable and maintainable.

    [
        'name' => $name,
        'age' => $age,
        'email' => $email,
    ] = $person;


This will assign the values of the array to the variables. This is a very simple example, but it can be used in more complex scenarios.

Let's see a more complex example and how you maybe doing it at the moment and how you can improve it using array spreading and destructuring.

function hello($name, $age, $email) {
    return "Hello, my name is $name and I'm $age years old. My email is $email.";
}

    $person = [
        'name' => 'John Doe',
        'age' => 30,
        'email' => 'john.doe@example.com',
    ];

    echo hello($person['name'], $person['age'], $person['email']);

This will work, but it's not the best way to do it. We can use array spreading and destructuring to make this code more readable and maintainable.

    echo hello(...$person);

This will pass the values of the array as arguments to the function.

Very cool, right?

One other thing I like to do is maybe add some conditions to the array spreading and destructuring. Let's imagine I want to add some elements to the array, but only if the user has a specific role.

    $person = [
        'name' => 'John Doe',
        'age' => 30,
        'email' => 'john.doe@example.com',
        ...$user->role === 'admin' ? [
            'permissions' => ['create', 'read', 'update', 'delete']
        ] : [],
    ];

This will add the permissions to the array if the user has the role of admin.

These are just a few examples of how you can use array spreading and destructuring in PHP. I hope you found this useful and that you will start using these features in your projects.
