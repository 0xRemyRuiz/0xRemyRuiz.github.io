---
title: "Pseudo-Infinite Calculator"
date: 2026-05-02T10:03:17+02:00
draft: false
tags: ["Dev", "Maths", "Python"]
description: "A relatively simple project to improve my Python skills"
---

## Creating a pseudo-infinite naive calculator

A post about getting a little better in Python using a toy project.

This post is written long after the fact. I started it in early june 2024, at that time I was thinking about abandoning my cybersecurity career change as, at the time, opportunities were scarce. So I thought I might as well improve in python so that I could be able to come back to dev jobs or stay focused on cybersecurity as the language is immensely popular in the field as well. Python is also very important in AI. The idea for this project is simply a "reboot" of an Epitech exercise which I did back then and I knew it was an "easy" but interesting one.

[Link to the project.](https://github.com/0xRemyRuiz/ASi_calculator)

## Starting without git, just for fun

Starting a project without git isn't a good idea, even when working solo on a project. You might start a refactoring but regret it. You might need to test something without crippling you main code. Anyway, a great lesson I learned through time and my failed experiments.

__`You better start dirty than don't.`__

This pseudo-philosophy helped me a lot making projects whereas before, often times I wanted to start creating the repo, then thinking about boilerplate, builders (at the time it was webpack for frontend), etc. Applying that mentality in work is paramount, but when you apply that to your fun personal projects, it might make you lose time and energy but it depends also on your mentality. It does work for me and that's what matters. Do the things that help you avoid procrastinating.

## First thing first

I won't enter into all the details but I'd like to elaborate on my process a little bit anyway.

First you need to build essential functionalities. Here it's the basic operations, `add`, `sub`, `mul`, `div`. So that we can iterate and start building our first batch of unit tests. Unit tests are mandatory nowadays and for good reasons, but here it is crucial and easy to do. We might think to ourselves "oh I'm building a todo app, I don't need unit tests" and we might be right if we don't have any necessity, if it's just a learning project. But here, the calculations have to be precise and never deviate or else the whole project fails. To me, there are 3 majors cases where tests are absolutely critical.

1. Precision matters
2. Integration matters
3. Project size is huge

For the integration part, it's when you will need to integrate your project into something else. For instance, one of my older projects (way older) was an Arduino program to control a custom-made electronic circuit controllable using 2 buttons and an LCD display. The thing is that I had to develop the pseudo-firmware without any access to material which was bought by my nephew. So I had to make sure my code was rock solid so when we could see each other and test integration, we wouldn't need to debug the code but rather the physical details to bind those together. I had to make a custom virtual screen to test the interface in a local terminal. I also had to write unit tests to make sure base logic works as expected. Someday I might publish it back here as it is still on my previous GitHub account.

The file dedicated to basic operations is simply labeled `basic.py`. The tests are in `tests.py` obviously. I could have used the default `unittest` python framework but at the time I didn't know I would like the project and go so far. My first tests were very basic, I added the `test()` function wrapped after I started to add many cases and the `calc()` function if I recall well. Again, this project suffers from the absence of an early repo.

## Getting serious

At one time I started wanting more since I was getting good results relatively fast. I need a solid `calc()` function to be called simply and I could have used the [reverse polish notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation) but opted for a basic linked list. The 3 main reasons are, it was easier for me to implement (less mental gymnastic, instant implementation), it was preferable (I love working with chained lists) and it was a more "generic" concept to work with. But one day I might try to finish a version using RPN. It's just a lot of work with many different operators with many different priorities and no real base reference available (at least I didn't find one). I needed new tests to make sure the pseudo-[AST](https://en.wikipedia.org/wiki/Abstract_syntax_tree) works as expected. I also needed a basic [CLI](https://en.wikipedia.org/wiki/Command-line_interface) so that I could some [e2e](https://en.wikipedia.org/wiki/End-to-end_principle) tests dynamically and also so I could show my family and friends what I did during that time. The `client.py` serves that purpose and I also added some ASCII banners (cf `banner.py`) to make it a little more pretty and fun.

## Conclusion

I skip the part about my crazy experiments calculating [π](https://en.wikipedia.org/wiki/Pi) using some black magic also known as the [Chudnovsky algorithm](https://en.wikipedia.org/wiki/Chudnovsky_algorithm). I skip the part when I got into calculating square root, nth root and started researching doing those with floating point numbers. I looked at implementing neperian logarithm, power of n with floating points. I'm not a math guy so that started to take me into a damn deep rabbit hole. You can find a none exhaustive Roadmap in the Readme [here](https://github.com/0xRemyRuiz/ASi_calculator/blob/main/README.rst#roadmap).
