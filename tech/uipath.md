% UiPath Doc

<link id="linkstyle" rel="stylesheet" href="markdown.css"/>

# Intro #

## Main Types ##

* Sequences
  suitable to linear processes, enabling you to smoothly go from on activity to another, without cluttering 
  your project.

* Flowcharts
  suitable to a more complex business logic, enabling you to integrate decisions and connect activities in a more
  diverse manner, through multiple branching logic operators.

* State Machine
  suitable for very large projects. They use a finite number of states in their execution which are triggered by
  a condition or activity.

#  #


-------------------------------------------------------------------------------

# UIPath fundamental #
* Studio
作为后台创建Process，并发布到Orchestrator上。
* Robot
分成两种不同的定义
    + Attanded Robot 一般用于人机互动的流程，手动触发。
    + Unattanded Robot 常封装于VM上，在Orchestrator上设置固定启动时间定点触发。

* Orchestrator
使用Studio开发完一个流程后，一般会将其发布到一个Orchestrator。

# workflow #

* Sequences
* Flowcart
* StateMahine

## 变量 ##

### 属性 ###

* Name
* Type
  + Boolean
  + Int32
  + String
  + Object
  + Generic Value 
    泛型
  + Array Of [T]
  + Browse for Types 
    类型库
* Scope
* Default

## 输入输出 ##

## Selector ##

#### Selector Editor####

### 通配符 ###

### UI Explorer ###

## Excel和数据表自动化 ##

### Excel类Activity ###
* Excel下的所有activities都必须包含在Excel application scope这个activity内才可以使用
* 默认会打开Excel进程，可以通过设置Visible属性选择不显示Excel文档。

### Workbook类Activity ###
* 在与Excel类文档相比中，推荐使用Workbook类Activity。因为不需要打开Excel进程。

### 基本操作 ###

* Read Cell, Write Cell
* Read Range, Write Range
* Read Column, Read Row
* Append Range

### 实例 ###

1. Read Range读取表格
2. Build Data Table根据需要创建一个数据表
3. For Each Row
4. Write Range

### Lookup Data Table ###

* Input
  + LookupValue
  可以通过Read Range读取，LookupValue是我们要查找的值，可以是常量也可以是变量
* Lookup Column
  + Column
  + ColumnIndex
  + ColumnName
* Output
  + RowIndex
  + CellValue
* Target Column
  Target Column是我们要查找的值在查找区域所在行对应的列，类似Lookup Column，对应列也可以通过一样的方法指定，这边就不赘述了。


## 键盘, 鼠标UI交互 ##

### Click, Double Click ###
目标可以通过 Indicate On Screen功能自动生成，该功能试图标识指定区域中的UI元素，并为其生成Selector(UiPath基础篇 - 初识Selector)。如果这对指定目标不起作用，则可能需要手动干预（UiPath基础篇 - Selector进阶1）。

### Hover ###
模拟鼠标在指定目标上悬停。

### Type into, Type Secure Text ###

### Send Hotkey ###

### Set Focus ###

## 文本自动化 ##

在某些特殊情况下，UI元素无法通过标准方法进行标识，这时候文本自动化相关的activity则能够根据它们包含的文本，去识别按钮、复选框和其它UI元素。

### Click Text, Hover Text ###

### Get Full Text ###

### Text Exist ###

### Extract Structured Data ###


## 图像自动化 ##

### Click Image, Hover Image ###

### Find Image ###

等待指定图像出现后再执行下一步activity。

### Image Exist ###

用于验证屏幕上是否存在某个指定图像。它会返回一个布尔变量，该变量声明是否找到了该图像。
和Find Image相似，能够根据给定的图像是否显示，或者通过将其用作Retry Scope activity的条件，为在循环中执行某些操作来做出决策。

### On Image Apprear ###

### On Image Vanish ###

## PDF ##

### Read PDF Text ###


