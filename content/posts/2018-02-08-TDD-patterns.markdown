---
layout: post
comments: true
title: Test-Driven Development Patterns
date: 2018-02-08 16:39:00
description: Improving TDD Skills
---


I recently began reading Test-Driven Development By Example by Kent Beck and I can't say enough about the book. If you haven't 
read it, I would highly recommend it. 

Prior to my apprenticeship, I knew Test-Driven Development was considered a best-practice. In the field of social work, my prior profession, there is a very strong committment evidence-based practice. Evidence-based practice means that a particular treatment or methodology has been established as effective through scientific research. Put simply, it means the practice has been proven to work. The same applies for TDD (not the scientific part) and it has been a skill that I've wanted to improve on since I started programming. 

When I would come across a problem I was familiar with using a language I was comfortable with, TDD seemed easy to do. I won't say I always take the smallest steps possible, I'm still working on that. But when I'm faced with something I'm unfamiliar with or I'm unsure how to proceed I tend to struggle truly test-driving my code. Ironically, this is when TDD is the most helpful! Kent Beck says, Test-Driven Development is a way of managing fear during 
development. 

What I knew about TDD was pretty simple: Red/Green/Refactor. Write a failing test, write some code to make it pass, refactor to remove duplication. In it's most basic form that does sum up TDD. However, what I want to talk about are some patterns and tidbits of advice that I've picked up from reading TDD by Kent Beck. 

_Note: This is not an inclusive list of patterns just some patterns I thought were exceptionally helpful in improving TDD skills._

### **TDD Patterns**
<br>

#### **Test List** 
<br>
This almost seems so simplistic and inherent for some but this was a sticking point for me. Before you begin, write a list of all the tests you know you will have to write. **Think about what it is you need to accomplish**. This helps you avoid holding all those thoughts in your head and programming on a whim. It doesn't have to just be a list of tests either, it can include things you want to refactor in order to have clean code. I'm guilty of trying to hold all of my ideas in my head when I get excited and try to code them before I forget. That strategy, as you've probably guessed, doesn't work out so well. 


#### **Assert First**
<br>
When should you write the assertions? Write them first! If you write your assertions first you get to work backward and don't necessarily have to think about the implementations or how it's all going to work. All you need to ask is: "What is the right answer" and "How am I going to check?". From there you can start working backwards and connect the dots. When I have a hard time writing a test it's usually because I'm thinking about the implementation instead of "How am I going to check?" which causes me to get stuck. 

#### **Test Data**
<br>
What data do you use for tests? Use data that makes tests easy to read and follow. Don't scatter random data values around, try to make them meaningful. **You are writing tests for a reader, not a computer**. I think that sentence is an important one. Up until now, I considered tests just to be something I wrote to ensure my code worked. I didn't necessarily consider that my tests should be readable for other people. 


### **Red Bar Patterns**
<br>

#### **One Step Test**
<br>
So assuming we starting using a Test List, how do we decide which test we should pick next from our list? Pick a test that you are confident you can implement quickly. If you don't happen to find a test like that on your list, then add some tests that would represent progress towards one of those items. 


#### **Another Test**
<br>
When a new idea arises, add it to your list and go back to the topic at hand. It's easy to get distracted when an exciting idea comes to you or you get a breakthrough, trust me I know! But before you know it you've been hopping around to different things for an hour and lost track of what you intended to work on. 

#### **Regression Test**
<br>
What's the first thing you do when a defect is reported? Write the smallest possible test that fails and repair it. Ok, that's pretty sensible but one thing that Kent Beck says is "Regression tests are test that, with perfect foreknowledge, you would have written when coding originally. Every time you have to write a regression test, think about how you could have known to write the test in the first place." A regression test can easily be added and you can move along but I think it's important to take a few seconds to reflect and think about what you could have done differently. 

### **Green Bar Patterns**
<br>

#### **Fake It**
<br>
What is your first implementation once you have a failing test? Return a string or integer. Once the test is green, turn the string or integer into an expression using variables. This one is difficult for me to do because I know in a few minutes I'm going to delete that code and write something better so why bother? Well, it can help starting with a concrete example and generalizing as you go without prematurely concerning yourself with extraneous concerns. It helps you solve the **immediate** problem and stay focused. 

#### **Triangulate**
<br>
How do you most conservatively drive abstraction with tests? Only generalize when you have two or more examples. Once you have two assertions for a function and you have abstracted the correct implementation then you can delete one of the tests. This can help when you are unsure how to proceed or don't quite know the correct abstraction. 

#### **Obvious Implementation**
<br> 
This is pretty obvious (no pun intended) but if you know how to implement a simple operation then implement it. None of these patterns have to be used exclusively, you can switch back and forth depending on the type of problem you are facing. I find this to be more dangerous personally because I might **think** I know the implementation but that's not always the case. Practicing smaller steps using Fake It and Triangulation I think are important if you are trying to become better at TDD. 

<br>

As I start working on a new project in the coming days I plan to apply these new (to me) patterns and hone in on my test-driven development skills. 
