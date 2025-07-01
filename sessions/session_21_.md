Types of Inheritance
    1. Single Inheritance: A class acquiring properties from only one super class.
    2. Multipel inheritance: A class acquiring peroperites from more theatn one entity.
        Note: In ABAP, Multiple inheritance canbe implemented using the combination of class and interfaces.
    3. Multilevel Inheritance: A class acquiring the propeties from another sub-class.

    Inheriting from: is a keyword used as part of local class definition for inheriting another class.
    A class declared as Final cannot be inherited i.e. it cannot have subclass. In case of local classes, we use the keyword 'final' as part of class definition to declare a final class.


Polymorphism:
    Poly -> many,
    Morph-> forms,
    Ism  -> behaviour

    * It is a process of making an entity behaving in multiple forms,
    * In this case, the entity is a method.
    
    Example: 
        Method overloading, Method Overriding.
    
    Method Overloading:
        * It is similar to function overloading in C++.
        * It is a process of overloading the same mehtod by passing different Number and Different types of parameters.

        Eg. methods m1.
            Methods m1 importing x type i.
            Methods m1 importing x type c.
            Methods m1 importing x type l_y type i.

            Note: ABAP does not support method overloading.
        
    Method







Abstract Class:
    Abstract is a class which contains one or more Abstract Methods.
    An abstract method is a method which is jist declared but not implemented.
    We declare a method as abstract when we are not sure about the implementation.
    The implementation for the abstract methods can be provided as part of subclasses.
    In local classes, abstract methods are declared by using a keyword "abstract".
    If a class contains an abstract method, the class also should be declared as abstract.
    Abstract methods are declared only in public and protected sections.
    