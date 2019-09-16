---
layout: default
title: Tech
permalink: /tech/
---

# Motivation
We treat students like compilers. We want them to simulate the action of the compiler when they are tracing code. We talk about concepts in programming using the language of a compiler (for loops are one concept, if statements are another concept). Do students really think that way?

# NoviceParser

NoviceParser is a tool that models the ability of a student to correctly answer a question, based on prior exposure to similar problems. NoviceParser is trained on the problems that students have completed in their curriculum. Using a lexer and parser, NoviceParser identifies patterns within each problem. NoviceParser tracks the number of times each pattern is seen across the curriculum. Then, this data is used to give new problems an “exposure” score that predicts how likely a student would be to get that problem correct. 

NoviceParser analysis creates an opportunity for different definitions of patterns to be compared head-to-head. Rules in NoviceParser can be arbitrarily defined by changing the lexer and parsing rules. Is one type of pattern definition more predictive of student success than another?

We created two versions of NoviceParser to compare two perspectives on how novices understand code. In the first version of NoviceParser, we used the standard lexing and parsing rules from a typical C compiler. In the other version of the lexer and parser, there are more specific rules which we see as reflecting the “human” understanding of programming patterns. These rules incorporate more information about the position of an expression, so that the same expression in different locations counts as different rules. More details about these patterns can be found in section X. We ran our two versions of the NoviceParser on the same data set, and compared the accuracy of the exposure scores. 

![workflow](../workflow.png)

# Implementation details
SLY, for C-like languages, etc.
The lexer and the parser are both implemented in Python, using the SLY library. The parser works with C-like languages.

# Lexing

The lexer is written in python and uses the library sly. Sly is a library that helps with writing parsers and compilers. The lexer runs through the input of a program/problem and would store each part of the problem into tokens. These tokens hold parts of the patterns which are used within the input program. The tokens are variables, operations used on the variables, parameter types, boolean operators, etc. The tokens are then stored to be used within the parser afterwards to further analyze the program to produce the exposure score. 

# Parsing

After the data file is sent through the lexer, the tokens are sent from the lexer and is used through the parser. In the parser the tokens are analyzed further to put together the different parts of the code. This would examine the different tokens and what the code does with different assignments, variables, etc. For example, the parser would find all of the expressions which contain different calculator operations, look for different variable declarations, etc. 

# Exposure score

The exposure score is produced by our NoviceParser after it has taken in an input of problems that the students have seen in their curriculum. The exposure score is given to an assessment problem in which the student could see on an exam in the future. This exposure score would model how students would do on the problem to see if many of the students would get the problem wrong or right. 

Two different exposure scores that are produced are each assessment problem that is analyzed through the NoviceParser. One of the scores would be produced by standard compiler rules while the other is produced by the human compiler rules. Each of these sets of rules have the lexer and parser run differently as to differentiate from the two sets of rules. These two exposure scores are compared with one another to gauge whether our human compiler rules have a better prediction of how novice programmers understand patterns rather than the standard rules. 

[Home page](../)
