---
layout: post
title:  "Deep Dive into Java Memory Managment"
date:   2018-08-22 09:06:00 +0530
categories: Java
---
In this article, we will be discussing Java Virtual Machine (JVM), understanding memory management, memory monitoring tools, monitoring of memory usage, and Garbage Collection (GC) activities.

Lets get started!!!

## Java Virtual Machine (JVM)

The JVM is an abstract computing machine that enables a computer to run a Java program. There are three notions of JVM: specification (where working of JVM is specified. But the implementation has been provided by Sun and other companies), implementation (known as (JRE) Java Runtime Environment) and instance (after writing Java command, to run Java class, an instance of JVM is created).

The JVM loads the code, verifies the code, executes the code, manages memory (this includes allocating memory from the Operating System (OS), managing Java allocation including heap compaction and removal of garbage objects) and finally provides the runtime environment.

## Java (JVM) Memory Structure


JVM memory is divided into multiple parts: Heap Memory, Non-Heap Memory, and Other.
