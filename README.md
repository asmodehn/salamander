# salamander

Self Healing Python
================

This is currently a small experiment with python self healing code.
When you write python code, you (should) write the main code, the tests and the documentation in a way that they all match each other.

Many programmers write the code first, the tests second, and the documentation last.
While this is fine when you start building your application, it quickly leads to inconsistencies between these three, as most of us never have the time to maintain all of it.

Test Driven Development advocates for developing the tests first. However this is something that many don't have the liberty to in practice (ex: Companies short term focus means they only care about the code)

Following that logic ( and a century or two of industry experience ) indicates that writing code should actually be writing Documentation/Specification first, and have everything follow from there (tests then code).
However generating code from documentation is something that is still in the realm of utopia since the great many details that need human interpretation before going into production code.

In this day and age where everything needs to be more flexible, more quickly changeable, and overall very agile, many people see documentation and even tests as a waste of time.

This project aims at inverting the flow and fixing the way programming is done by making it easier and faster to do it properly.
The goal is for a programmer to write the test, with documentation, and the code gets modified (with documentation).

It is a python project because python is a widely used and popular language with many tools, and also exposes its internal organs to mess around with...

Quick First Step Design
--------------------

We need to base ourselves on something simple and stable : the function.
We will temporarily ignore cases with side effects.

- a function f does _something_
- multiple tests functions verify that f conforms to its specification ( including the documentation )
- salamander analyse the test runs, and modify the existing **source code** (not the bytecode) in order to "propose" changes to the developer.

The analysis is kept very simple for now :
- a function that return is fine.
- a function that except needs fixing. we rely on the basic python exceptions.

First we focus on how salamander can interract with python source code without being an hindrance to the programmer

Salamander **does not** :
- modify the tests. Instead it proposes modification to the code if unsure where the problem comes from.
- modify the code in an non deterministic way
