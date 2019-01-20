---
layout: post
title: "tutorials_glibc"
date: 1970-01-01
---



The glibc library is the most important library in linux because it is responsible for cross linking all the applications which has used C or C++ as their programming language. This makes almost every development done in C, C++ to embed this library, commonly by the option -lc.

However, by removing the glibc library, the kernel will still find its dependancies, because the kernel itself has its own set of libraries. Users do not use the kernel libraries until and unless ofcourse, they are developing the kernel.

