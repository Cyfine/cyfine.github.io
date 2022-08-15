---
title: "Regular Expression"
date: 2022-08-15T23:20:45+08:00
draft: false
author: "Carter Yifeng CHENG"
description: ""
summary: ""
tags: ["regex"]
categories: [""]
---
The regular expression is an **algebraic expression** for text search strings. It defines a representation to match a set of strings. 

The basic format of regex is `/<regex>/` e.g. /love/ matches <u>love</u>r, but not Love. Regex is case-sensitive. 

## Disjunction of  A character

The `[]` is used to represent character disjunction (or). e.g. `/l[ai]ke/` matches <u>like</u>, <u>lack</u>. The place at the second character is either `i` or `a`. 

### Match a range of characters

Inside the `[]`, using `-` can represent a range of characters, for instance. [a-z] is a lower case letter from a to z. `/[A-Za-z0-9]/` represents numerical digits, upper case letters, and lower case letters. 

### Indicate not some characters

Inside `[]` using,  the caret `^` right after  `[` can be used to match characters that are not the specific set of characters. e.g. `\[^a]\` matches all characters except for a.  e.g.  `/[^0-9]/` matches 90 `<u>k</u>ilogram`. (here only underscore the first matched character). 

To be mentioned, if the caret `^` is not right after `[` inside of square brackets, it is only a caret! When outside of square brackets, `/\^/` matches `^`

## The counters and wildcard expression

### Counters

The counter is being used to indicate how many times the pattern before them should repeat in a matched token. 

| Expression | Meaning                                                      |
| ---------- | ------------------------------------------------------------ |
| ?          | 0 or 1 times                                                 |
| +          | 1 or more times                                              |
| *          | 0 or more times                                              |
| {<l>,<u>}  | at least l times, at most u times. If l and u leave empty, e.g.`{2,}`/`{,2}`indicates at least/most two times. |
| {<k>}      | the pattern should repeat exact k times                      |

The counter should be placed at the end of the pattern. e.g. /a+/ matches <u>a</u>pple, <u>aaa</u>. 

### Wildcard expression (通配符)

`/./` is the wildcard expression, which represents any characters, except the carriage return.

## Anchors

| Expression | Meaning                  |
| ---------- | ------------------------ |
| ^          | Start of the line anchor |
| $          | End of the line          |
| \b         | word boundary            |
| \B         | not a word boundary      |

## Disjunction, Grouping, and Precedence

### disjunction

`|` is called the disjunction operator, also called the pipe symbol, which means "or". 

`/cat|dog/` matches the word `cat` ,`dog`.

### group

Group is being indicated using `()`, which is a string of characters that behaves atomically like a single character.

For instance  /the(re)?/ matches <u>the</u> and <u>there</u>. 

### precedence

1. () 
2. counters 
3. sequences and anchor
4. disjunction `|`


