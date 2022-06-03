---
title: Scientific programming languages
subtitle: 

# Summary for listings and search engines
summary: 

# Link this post with a project
projects: []

# Date published
date: '2022-05-26T00:00:00Z'

# Date updated
lastmod: '2022-05-26T00:00:00Z'

# Is this an unpublished draft?
draft: false

# Show this page in the Featured widget?
featured: false

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
image:
  caption: 
  focal_point: ''
  placement: 2
  preview_only: false

authors:
  - admin

tags:
  - Academic

categories:
  - Demo
---

## **Introduction**

A programming language is a formal language for writing computer programs. A programming language defines a set of lexical, syntactic and semantic rules that determine the appearance of the program and the actions that the performer (usually a computer) will perform under its control.

Since the creation of the first programmable machines, mankind has come up with more than eight thousand programming languages ​​(including esoteric, visual and toy ones). Every year their number increases. Some languages ​​are used only by a small number of their own developers, others become known to millions of people. Professional programmers may be proficient in several programming languages.

A programming language is intended for writing computer programs, which are a set of rules that allow a computer to perform a particular computational process, organize control of various objects, etc. A programming language differs from natural languages ​​in that it is designed to control a computer, while how natural languages ​​are used primarily for communication between people. Most programming languages ​​use special constructs to define and manipulate data structures and control the process of computation.

As a rule, a programming language is defined not only through the specifications of the language standard, which formally define its syntax and semantics [⇨], but also through the incarnations (implementations) of the standard - software tools that provide translation or interpretation of programs in this language [⇨]; such software tools differ by manufacturer, brand and variant (version), release time, completeness of the implementation of the standard, additional features; may have certain errors or implementation features that affect the practice of using the language or even its standard.


## **Low and high level languages**

Typically, "language level" refers to:

the degree of difference between the semantics of the language and the machine code of the target processor architecture - in other words, the smallest scale of transformations that the program code must undergo before it can be executed (often with a significant loss of efficiency)
the degree to which the semantics of the language takes into account the peculiarities of human thinking, rather than machines - that is, the level of the language is the "lower", the closer it is to the machine, and the "higher", the closer it is to the person.
This duality appeared in the 1950s, with the creation of the Plankalkül and Fortran languages. During their development, direct intentions were set to provide a more concise record of frequently encountered constructs (for example, arithmetic expressions) than was required by the processors of that time. These languages ​​introduced a new layer of abstraction and assumed the transformation of programs into machine language, so they were called "high-level" languages, that is, a superstructure, a layer above the machine language. However, it soon became clear that these definitions do not necessarily go side by side. Thus, history knows cases when a language traditionally considered "high-level" was implemented in hardware (see Lisp Machine, Java Optimized Processor [en]), or when a language that is "low-level" on one platform was compiled as "high-level" on another (this is how VAX CISC assembler programs were used on DEC Alpha RISC machines - see VAX Macro[en]). Thus, the concept of language level is not strictly formal, but rather conditional.

Low-level languages ​​include, first of all, machine languages ​​(or, in common jargon, machine codes), that is, languages ​​implemented directly at the hardware level. They belong to the first generation of programming languages[en]. Shortly after them, second-generation languages[en] appeared - the so-called "assembler languages". In the simplest case, they implement a machine language mnemonic for writing commands and their parameters (in particular, addresses in memory). In addition, many assembly languages ​​include a highly developed macro language. The languages ​​of the first and second generation allow you to precisely control how the required functionality will be executed on a given processor, taking into account the features of its architecture. On the one hand, this ensures high speed and compactness of programs, but on the other hand, in order to transfer a program to another hardware platform, it needs to be recoded (and often redesigned due to differences in processor architecture) from scratch. Most assembly languages ​​are typeless, but there are also typed assembly languages[en] aimed at providing a minimum security>>> of low-level programs.

By the 1970s, the complexity of programs had grown so much that it exceeded the ability of programmers to manage them, and this led to huge losses and stagnation in the development of information technology. The answer to this problem has been the emergence of a mass of high-level languages ​​that offer a variety of ways to manage complexity (for more details, see the programming paradigm and languages ​​for programming at small and large scales). Programs in "high-level" languages ​​are much easier to modify and very easy to transfer from computer to computer. In practice, third-generation languages, which only claim to be “high-level”, but actually provide only those “high-level” constructions that find a one-to-one correspondence with the instructions in the von Neumann machine, are most widely used.

The languages ​​of the fourth generation include higher-order languages>>>. Sometimes a category of fifth-generation languages ​​is distinguished, but it is not generally accepted - the term “very high level language” is more often used. These are languages ​​whose implementation includes a significant algorithmic component (that is, where the interpretation of a small source code requires very complex calculations). Most often, this is the name of logical languages, which are also said to be just fourth-generation languages, supplemented by a knowledge base. In addition, "high-level languages" include visual languages ​​and languages ​​based on a subset of natural language (for example, the so-called "business prose").

An important category is domain-specific languages ​​(DSL - Domain Specific Language). The assignment of a language to this category is highly arbitrary and often controversial; in practice, this term can be applied to representatives of the third, fourth, and fifth generations of languages. Sometimes they even classify the C language, which can be attributed to the “2.5” generation. It was originally marketed as "high-level assembler"; it is also often referred to as an "intermediate-level language". It allows you to largely control the way the algorithm is implemented, taking into account the properties typical of a very large number of hardware architectures. However, there are platforms for which there are no C implementations (even in a non-standard form) due to the fundamental impossibility or inexpediency of their creation. Over time, other middle-level languages ​​appeared, for example, LLVM, C--.

The first three generations of languages ​​form an imperative programming paradigm, and subsequent generations form a declarative one. The term "imperative" means "command order", that is, programming by means of step-by-step instruction of the machine, or a detailed indication of the way the programmer has already invented for the implementation of the technical task. The term "declarative" means "description", that is, programming by providing a formalization of the terms of reference in a form suitable for automatic transformations[en], with the freedom of choice for the language translator. Imperative languages ​​aim at describing how to get a result, while higher-level languages ​​aim at describing what is required as a result. Therefore, the former are called how-languages ​​(or machine-oriented languages), and the latter are what-languages ​​(or human-oriented languages). For many problems, a fully automatic generation of a truly efficient implementation is algorithmically undecidable, so in practice, even in what-languages, certain algorithmic tricks are often used. However, there are methods for obtaining efficient implementations from definition-based (head-on implementations) - such as supercompilation invented in the USSR.

In most cases, high-level languages ​​produce larger machine code and run slower. However, some high-level languages ​​for algorithmically and structurally complex programs can provide a noticeable advantage in efficiency, yielding to low-level ones only in small and simple programs (see Language Efficiency for more details). In other words, the potential efficiency of a language changes with an increase in its “level” non-linearly and generally ambiguously. However, the speed of development and the complexity of modification, stability and other quality indicators in complex systems turn out to be much more important than the maximum possible speed of execution - they provide a distinction between a program that works and one that does not - so that the evolution of hardware is more economically feasible (execution of more instructions per unit of time) and optimizing compilation methods (moreover, over the past decades, the evolution of hardware has been moving towards supporting optimizing compilation methods for high-level languages). For example, automatic garbage collection, which is present in most high-level programming languages, is considered one of the most important improvements that have a beneficial effect on development speed.

Therefore, these days, low-level languages ​​are used only in system programming tasks.