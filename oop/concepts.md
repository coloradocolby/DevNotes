# Object Oriented Programming Concepts

## Class vs Object

A class is a blueprint. The blueprint doesn’t do anything, just gives instructions on how to make something tangible (an object);

When we want to make something from that blueprint, that thing is an object.

We can use the class to make multiple objects. Each object would inherit everything from the class they were built from.


## Inheritance

Incredibly important, mainly to save our own time.

Let’s say we write a class to create a car. Our car has wheels, doors, and driver name. Now we create another class to create a truck. Our truck also needs wheels, doors and driver name.  Not only are our properties similar, they’re all the same. To write them separately we’d have to write things twice. This is bad practice!

Inheritance allows us to use the properties of existing class. 

Base class called vehicle = wheels, doors, driver name.

From that we create car class which inherits from vehicle

Inherit means gets all properties and methods immediately available to it. (We don’t have to write them out again)

In the car we automatically have wheels, doors, and driver name.

We can further give care functions and properties that are specific just to cars (and not to trucks)

Now our car class might have a numberOfPassengers property because that’s inherent to it. However, our truck class might have a property called carriedWeight.

Inheritance is like evolution. Child classes branch out from their base (or Parent) classes to become more specialized.

You can also have multiple inheritances at play. So even though our car class is a child of the vehicle class, it can have its own minivan subclass. Important to note, the minivan subclass will still inherit the wheels, doors, and driver name all the way from its grandparent class!


## Polymorphism

Let’s say we have a block of code that takes in input and spits out output. If we put in a different type of input however, our code will break since it’s not build to handle it. Polymorphism takes care of this.

Polymorphism is effectively writing multiple copies of the code. Each version takes in different inputs.

For example, a `speak()` function takes in a dog and outputs woof, a cat and outputs meow, and cow and outputs moo.

Polymorphism is writing the same block of code, and most importantly, giving it the same name, but allowing it to take a slightly different argument. Then our program knows if I give ‘dog’ to speak, the program knows which particular code to use.

Using one bock of code, changing which version of that block of code we are using depending on what inputs we are giving it.


## Abstraction

Every block of code or function or method you write should do something, but that thing is relatively unimportant to the input and the output. I just want to give in some input and get out some output. I don’t care what goes on inside the code. Abstraction means hiding away functionality from the user or  programmer. When done right, abstraction means that everything becomes modular and re-usable.

The beauty of this is that say in 5 years you realize you coded your feature all wrong, you can go in and change it, and as long as your new code accepts the same inputs and emits the same outputs, nothing breaks.


## Encapsulation

Makes code much safer to execute. Imagine we have some variables and functions. If these were available to all of the software running in our program, we might be overwriting things or receiving values we never intended.

Encapsulation solves this by wrapping out things up inside classes. In our class we have variables and methods, and we can make these private. When our variables or methods are private, it means that other classes, functions, variables, cannot access them directly unless we make them public, or we allow the functions to change the variables themselves inside the class or the instance of that class (an object).

Encapsulation can happen inside of classes themselves.

Using `foo` inside of function `f()` and function `j()`, each `foo` would have no idea the other existed. One would be exclusively available to `f()` and the other to `j()`

Encapsulation allows you to encapsulate things that shouldn’t be modified by other parts of your code.