% Lisp dialects Tips

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[Emacs Lisp Reference](https://www.gnu.org/software/emacs/manual/html_node/elisp/)
[Xah Emacs Lisp](http://ergoemacs.org/emacs/elisp.html)

# 基础知识 #

``` emacs-lisp
(message "hello world")
```
运行在 *lisp-interaction-mode*

## 函数和变量 ##

## 局部作用域变量 ##

## lambda表达式 ##

## 控制结构 ##

### 顺序执行 ###

### 条件判断 ###

### 循环 ###

## 逻辑运算 ##

## 函数表达式 ##

# 基本数据类型 #

## 数字 ##

## 字符和字符串 ##

## cons cell和列表 ##

## 序列和数组 ##

## 符号 ##

# 求值规则 #

# 变量 #

# 函数和命令 #

# 正则表达式 #

# 操作对象 #

## 缓冲区 ##

## 窗口 ##

## 文件 ##


-------------------------------------------------------------------------------

Xah Emacs Lisp
==============

Lisp Basics
-----------

### Elisp Basics ###

Printing

* Printing
``` elisp
(message "Hello World!!!")
(message "Her age is: %d" 16)        ; %d is for number
(message "Her name is: %s" "Vicky")  ; %s is for string
(message "My list is: %S" (list 8 2 3))  ; %S is for any lisp expression
```

* Arithmetic
``` elisp
(+ 4 5 1)  ; 10
(- 9 2)    ; 7
(- 9 2 3)  ; 4
(* 2 3)    ; 6
(* 2 3 2)  ; 12

;; integer part of quotient
(/ 7 2)    ; 3

;; division
(/ 7 2.0)  ; 3.5

;; mod, remainder
(% 7 4)    ; 3

;; power; exponential
(expt 2 3) ; 8
```

* Convert String and Number

``` elisp
(string-to-number "3")
(number-to-string 3)
```

* True, False

``` elisp
(if nil "yes" "no")
(if () "yes" "no")
(if '() "yes" "no")
(if (list) "yes" "no") ; "no", because (list) eval to a empty list, same as ()

(if t "yes" "no")
(if () "yes" "no")
(if "" "yes" "no")
(if [] "yes" "no") ; "yes". The [] is vector of 0 elements
```

* Boolean Functions

``` elisp
(and t nil)
(or t nil)

(< 3 4)
(> 3 4)
(<= 3 4)
(>= 3 4)
(= 3 3)
(= 3 3.000000000000000000001)
(/= 3 4)
```

### Elisp Text-Processing Overview ###

### Elisp Example ###

### Evaluate Elisp Code ###

### Doc Lookup ###

### Search Doc ###

### How to Edit Lisp Code ###

Elisp Basic Functions
---------------------

Elisp: Writing Command
----------------------

Elisp, Writing Scripts
----------------------

Elisp Data Structure
--------------------

Elisp Symbol Topic
------------------

Elisp Misc
----------
