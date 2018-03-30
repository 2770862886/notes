UML Tips
======

# class
class A {
void method()
}
# Interface

# relation
## Generalization (泛化)
plantuml: Parent <|-- Child
## Realization (实现)
plantuml: Interface <|.. Implementation
## Composition (组合)
plantuml: Company *-- Department
plantuml: Class01 "1" *-- "many" Class02 : contains
## Aggregation (聚合)
plantuml: Car o-- Wheel
## Association (关联, 双向, 单向)
plantuml: Teacher -- Student
plantuml: Student --> Course
## Dependency (依赖)
plantuml: Human ..> Computer
