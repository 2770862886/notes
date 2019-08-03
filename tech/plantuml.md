% UML Tips

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[Official Website](http://plantuml.com/)
=======
Common Command
==============

Comment
-------

Footer & Header
---------------

Scale
-----

Title & Image title
-------------------

Image note
----------

Creole
------


UML Diagrams
============

时序图
------

用例图
------

类图
----

活动图
------

组件图
------

状态图
------

对象图
------


Gantt Diagram
=============

MindMap
=======

Breakdown Structrue
===================

Salt ui interface
=================


Sprites
=======

Skinparam
=========

## class ##

``` java
class A {
    void method()
}
```

## Interface ##

## Relation ##

### Generalization (泛化, 继承) ###

`plantuml: Parent <|-- Child`

### Realization (实现) ###

`plantuml: Interface <|.. Implementation`

### Composition (组合) ###

`plantuml: Company *-- Department`
`plantuml: Class01 "1" *-- "many" Class02 : contains`

### Aggregation (聚合) ###

`plantuml: Car o-- Wheel`

### Association (关联 [双向, 单向]) ###

`plantuml: Teacher -- Student`
`plantuml: Student --> Course`

### Dependency (依赖) ###

`plantuml: Human ..> Computer`
