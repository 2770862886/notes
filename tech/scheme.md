% Scheme (Racket) development

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[Yet Another Scheme Tutorial](http://deathking.github.io/yast-cn/)  

# What is Racket #

* a programming language - a dialect of Lisp and a descendant of Scheme;
* a family of programming languages - variants of Racket, and more;
* a set of tools - for using a family of programming languages.

## Racket main tools ##
* racket, the core compiler, interpreter, and run-time system;
* DrRacket, the programming environment; 
* raco, a command-line tool for executing Racket commands that install packages, build libraries, and more.

``` racket
#lang racket

(define (extract str)
    (substring str 4 7))
```

Script can be execute by:
``` shell
racket <src-filename>
```

Or: In Unix-link system, can be execute by:
``` racket
#! /usr/bin/env racket
```

But, this is not recommend for bad performance and unspecific error.
``` racket
(load "extract.rktl")
(extract "the cat is out of bag")
```

# Essentials #

## Simple Values ##

Racket values include numbers, booleans, strings, and byte strings.

## Simple Definitions and Expressions ##

A program module is writtenas

``` racket
#lang <language> <topform>*
```

Parentheses is necessary!!!
``` racket
(define (nobake flavor)
    string-append flavor "jello")
> (nobake "green")
"jello"
```

Identifiers are written immediately after open parentheses with no extra space, 
and closing parentheses never go on their own line.

Racket syntax for identifiers is especially liberal. Excluding the special characters

``` racket
() [] {} " , ' ` ; # | \

```

### Conditional with if, and or and cond ###

``` racket
(if (> 2 3)
    "bigger"
    "smaller")
```

``` racket
(define (reply s)
    (if (equal? "hello" (substring s 0 5))
        "hi"
        "huh?"))
> (reply "hello racket")
"hi!"

> (reply "asdf.asdf.asdf.asdf")
"huh?"
```

``` racket
(define (reply s)
    (if (string? s)
        (if (equal? "hello" (substring s 5 0))
            "hi!"
            "huh?")
        "hub?"))
```

Instead of duplicate the "hub?" case, this function is better written as

``` racket
(define (reply s)
    (if (if (string? s)
            (equal? "hello" (substring s 0 5))
            #f)
        "hi!"
        "huh?"))
```

``` racket
(define (reply-more s)
    (cond
        [(equal? "hello" (substring s 0 5))
        "hi!"]
        [(equal? "goodbye" (substring s 0 7))
        "bye!"]
        [(equal? "?" (substring s (- (string-length s) 1)))
        "I don't know"]
        [else "huh?"]))

> (reply-more "hello racket")
"hi!"

> (reply-more "goodbye racket")
"bye!"

> (reply-more "what is your favorite color?")
"I don't know"

> (reply-more "mine is lime green")
"huh?"

```

### Anonymous Functions with lambda ###

``` racket
(define (twice f v)
    (f (f v)))

(define (louder s)
    (string-append s "!"))

(twice louder "hello")

(twice (lambda (s)
    (string-append s "!")))
```

### Local Binding with define, let, and let* ###

``` racket
(define (converse s)
  (define (starts? s2) ; local to converse
    (define len2 (string-length s2))  ; local to starts?
    (and (>= (string-length s) len2)
         (equal? s2 (substring s 0 len2))))
  (cond
   [(starts? "hello") "hi!"]
   [(starts? "goodbye") "bye!"]
   [else "huh?"]))

(converse "hello!")
(converse "urp")
```

``` racket
(let ([x (random 4)]
      [0 (random 4)])
      (cond
      [(> x o) "X wins"]
      [(> o x) "O wins"]
      [else "cat's game"]))

"O wins"
```

``` racket
(let* ([x (random 4)]
       [o (random 4)]
       [diff (number->string (abs (- x o)))])
       (cond
       [(> x o) (string-append "X wins by " diff)]
       [(> o x) (string-append "O wins by " diff)]
       [else "cat's game"]))

"O wins by 2"
```

## List, Iteration, and Recursion ##

### Predefined List Loops ###

### List Iteration from Scratch ###

### Tail Recursion ###

### Recursion versus Iteration ###

## Pairs, Lists, and Racket Syntax ##

### Quoting Pairs and Symbol with quote ###

### Abbreviating quote with ' ###

### Lists and Racket Syntax ###



