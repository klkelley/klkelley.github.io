---
layout: post
comments: true
title: Functional Programming  
date: 2018-02-28 12:54:00
description: What's functional programming?  
---

For the past three weeks I've been "functional programming". Clojure is a functional language but what does
functional programming even mean? Well, that's what we're going to talk about. I've been throwing the term around for 
weeks with rather little understanding of what it really means. While not completely related to what 
functional programming is, it does make you think in a different way especially coming from an OOP
language. I can't count how many times I thought, "I've done this in Ruby and Java, I'll do a similar
implementation" just to quickly realize I need a new plan of attack because of the lack of loops, state, etc. 

Clojure was my first functional language meaning I've only used object-oriented languages up until now. OOP is a programming
paradigm based on the concept of "objects", which are data structures that contain data, in the form of fields, often known 
as attributes; and code, in the form of procedures, often known as methods. 

Functional programming, another programming paradigm, is the process of building software by composing pure functions, 
avoiding shared state, mutable data, and side-effects. There seems to be some common characteristics and core concepts behind functional programming 
so let's take a look at what some of those mean in order to better understand functional programming.

_Note: These concepts are language agnostic and are not specific to Clojure._


### Pure Functions & Side Effects 
<br>

Put simply, a pure function is a function which given the same inputs, it always returns the same output and has no side effects. 
This means that if I were to call `(sum 2 3)` it would **always** return the same value (also referred to as referential
transparency which I'll touch on later). 

A side effect is essentially a state change that occurs outsides a function's scope or has an observable interaction with its 
calling function besides returning a value. When functions are predictable and you know they won't modify a state outside 
the function itself, then the idea is that you have more confidence calling this function in any scenario. Some side effects
would include: printing to the console/screen, writing to a file, triggering any external process, etc. 

Just about every language supports pure functions considering it's hard to make `(sum 2 3)` impure but a functional programming language
is one that supports and encourages programming without side effects. 

Of course, at some point you will likely have to write an impure function but the idea is to minimize the amount
of impure functions. 


### Referential Transparency
<br>

I mentioned this when discussing pure functions. Pure functions are closely tied to the concept of referential transparency
which says that an expression is considered referentially transparent when it can be replaced with it's value. 

Take this for example: 



```clojure 
(defn add 
  [x y]
  (+ x y))

(def seven (add 3 4))
; => 7

(def seven 7)
; => 7 

  ```




There is no change in meaning when the expression is replaced with it's value. Typically, mathematical functions are
considered to be referentially transparent.

In contrast, here's an example that is not referentially transparent because it does not yield the same results with 
the same arguments. Any function that relies on `rand` would not be considered as referentially transparent. 



```clojure 
(defn random-function 
  []
  (if (> (rand) 0.5)
    "Learning about referential transparency"
    "Functional programming rocks"))
```



<br>

### First-Class & Higher Order Functions
<br>

For some reason these two concepts have intimidated me in the past. Sometimes things that *sound* complicated really aren't that 
complicated and it's something I constantly have to keep in mind. 

First-class functions aren't exclusive to functional languages (they're heavily used in JavaScript and some other languages) 
but they are a requirement of being functional. What's a first-class function, anyway? In order for a function to be first-
class, you have to be able to set it to a variable. This allows you to handles the function as if it were a data type. 


Higher order functions are functions that either take a function as an argument or return it as a result. An example of a
higher order functions include the `filter` function which accepts a function specifying how elements of a list should be filtered
and returns a new list. Similarly, the `map` function iterates over a collection and returns a new list based on the passed-in function
that specified how the data structure should be transformed. 

### Immutable Data
<br>

At first, the idea of immutable data seemed a little crazy. How am I suppose to get anything done if I can't change
data?! Well, it turns out, it's not all that crazy. In functional programming, rather than changing the data they take in, functions
take in data as input and produce new values as output. Same is to be said about variables, they are also immutable and cannot
be changed. You can create new ones but you can't modify existing ones. 

Say we wanted to add a value to a collection in Clojure, in this case placing a marker on a TTT board. We could do something like this: 



```clojure 
(defn place-move
  [board spot marker]
  (assoc board spot marker))
```



Which **almost** looks like its mutating the data structure but in reality it's just taking in the data as input and returning a new collection. 
See, it's not so bad!



### Recursion 
<br>


The first few days I was using Clojure I wanted to loop until I received valid user input. I googled for quite a bit trying to find an example that
used a loop but all I could find were examples using recursion. I actually think you can use a normal `loop` in Clojure but the point I'm
trying to make here is that recursion is a crucial aspect of functional languages, it's used in place of loops. Typically I have shyed away from using recursion due to lack
of understanding (maybe intimidation is more honest) but I'm proud to say I can't count the number of times I've used recursion in my recent Clojure project! 

Recursion is a function that calls itself therefore it acts as a loop executing the same code multiple times. But don't forget about your base case
to avoid infinite recursions! 


### Summary: Characteristics of FP 
<br>

* FP languages are designed on the concept of mathematical functions that use conditional expressions and recursion to perform computation
* FP supports higher-order functions 
* FP languages don't support flow controls like loop statements and instead support using the functions and functional calls
* Like OOP, FP languages do support popular concepts like abstraction, encapsulation, and polymorphism. 


### Some Advantages of FP
<br>

* Bug-free Code - Not that you'll never get a bug it's just harder because FP doesn't support state so there are no side-effect results. 
* Efficient Parallel & Concurrent Programming - Because FP languages have no mutable state, there are no state-change issues making parallelism easier. I will also note that parallelism in Clojure was a breeze. It was so easy I was unintentionally trying to make it harder. 
* You'll begin to think differently - Ok, this is more or less a "side effect" (no pun intended) of using an FP language but I'd consider it an advantage. 

### Final Thoughts
<br>


This was a broad overview of the characteristics and core concepts behind functional programming. Do you have to know them before using a functional language? No, but it 
helps. Some of this would have been nice to know prior to starting my Clojure project but I picked up some of it along the way unknowingly. If you haven't had
exposure to functional programming I'd highly recommend it. While Clojure is the only functional language I've used, I was amazed at how much fun I had and
I'm admittedly a little sad to be wrapping up my project this week. 




