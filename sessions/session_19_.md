What is OOPS?
    -> It stands for Object-Oriented Programming.
    -> It is based on objects.
    -> It follows Bottom-Up programming approach.
    -> It is based on real world.
    -> It provides on ral world.ss
    -> It provides data hiding so it is very secure.
    -> It proveds reusability feature.

What is a class?
   ->  A class is a collection iof objects. Classes don't consume any space in the memory.
   -> It is aused defined day type that act as a template for creating objects of the identical type.
   ->  A large nuber of objcts ca be cread sing the csame class. Therefore, class is consided as the blueprint for the object.

WHat is an object?
    -> An object is a real world entity which have properties and functionalities.
    -> Object is also called an instance of clas, Objects take some space in memory.


    Eg. Fruit is class and its objecs are mano, apple, bana.

What is the diffrenece betweeen a class and an object?

Class
It is collection of objects.
It does'nt take up space in memory.
class does not eixt physically
classes are declared just once


Object
It is an instance of a class.
It takes space in memory.
Object exist physically.
Objects can be declared as and when requierd.



Class:
It is collection of objects.
Class is used to combine data and metods.
class's objects are created on theheap memory.
A class can inherit another class.
A class has all members private by default.
Classes are ideal for larger or complex objects

Structure
Structure is acollectionof variables of different data types under a single unit
Strucrure is used to grouping data.
Structure's objects are created on the stack memory.
A structure can't inherit anotehr structure.
A structure has all mebers public by default
Structres are ideal for small and isolated model objects.


Following are the basic feacure of oops:-
    1). Inheritance
    2). Polymorphism
    3). Abstraction
    4). Encapsulations


OOABAP
ONJECT: Object is a runtime instance of a class.
    It is a collection of attributes or componenets oa class.
    The abap staement 'CREATEOBJECT' is used to create an object.
    
Syntax:
    Data: <ref_class> type ref to <class_name>
    CREATE Object<ref_class>

    here<ref_class> is a runtime instance of a class.

CLASS: It is used to describe of define an object which can contain different attributes or componentes such as types, data, methos, constants etc.
    Class are of two types,
        1. Global class
        2. Local class
    
    1. Global Class: The global classes are maintained in the class pool.
        The global class and the attributes can be reffered across teh system 
        The T-Code SE24 is used to work with global class.

    2. Local Class: The local class are defined and implemented inthe same progrma.

    Each class has two sections
        1). Definition Section
        2). Implementation Section

    Class Definition:
        This section is used to define or declaer the different attribute such as sdata objects , conastats, methods, etc

        Syntax: 
            *class definetion section
            CLASS <Class_name> Definition.


    Class Implementation:
        It is used to implement the methosd of a class

        The ABAP statement 'CLASS .....IMPLEMENTATION' is used to the methd of a class.

        Syntax:
        *class implementation
        CLASS< class_name > IMPELEMENTATION.
        *implement methos as a class
        METHOS:<method name>...
        *get data.
        SELECT
        ...........
        ..........
        ENDSELECT.
        ENDMETHOD
        ENDCLASS

        Note:   -> The ABAP statement 'TABLES' shouldn't be use within the clsses.
                -> The internal tables must not be declaere with headerline or occurs int hte class.
                -> The ABAP statemetn 'LIKE' cannot be used to define the data objects in the classes.
                -> The seleciton-screens of the report statement cannot be defined within the class.

        TYPE_REFTO staemet: theis staement is used to define the different type of objeccts such as classes, interfaces, BADI definitions etc.

        
            


CLASS zcl_car DEFINITION.
  PUBLIC SECTION.
    DATA: brand TYPE string,
          color TYPE string.

    METHODS: display_info,
             set_data IMPORTING i_brand TYPE string
                               i_color TYPE string.
ENDCLASS.



CLASS zcl_car IMPLEMENTATION.
  METHOD set_data.
    brand = i_brand.
    color = i_color.
  ENDMETHOD.
  METHOD display_info.
    WRITE: / 'Brand:', brand,
           / 'Color:', color.
  ENDMETHOD.

ENDCLASS.


# Visibility Sections and Types of Attributes in ABAP

## Visibility Sections

In ABAP, class components (attributes, methods, etc.) are grouped into three visibility sections:

### 1. Public Section
- Attributes declared in the `PUBLIC SECTION` can be accessed:
  - Within the same class
  - In all subclasses
  - From external classes (anywhere)

### 2. Protected Section
- Attributes declared in the `PROTECTED SECTION` can be accessed:
  - Within the same class
  - In all subclasses
- **Note:** They cannot be accessed from external classes.
- Use the ABAP statement `PROTECTED SECTION` to define protected attributes.

### 3. Private Section
- Attributes declared in the `PRIVATE SECTION` can only be accessed:
  - Within the same class
- **Note:** They cannot be accessed from subclasses or external classes.

---

## Types of Attributes

Attributes define the data stored within a class. They can be of the following types:

### 1. Instance Attributes
- Exist separately for **each instance** of a class.
- Declared using standard ABAP statements such as `DATA`.
- Accessed using the **instance reference** and the arrow symbol `->`.

#### Syntax:
```abap
CLASS <class_name> DEFINITION.
  PUBLIC SECTION.
    DATA: gv_var TYPE <data_element>.
ENDCLASS.







Following the different visibility section.
    Public Section
    Protected section
    Private section

    Public section attriction can be accedssed in the same class, sublacsses and external classes(anywhre).
    the abap 


    The attributes of aprotected section canbe accesssesd in the same class and suubcalssed only.
    the protected section attributes cannot be accessed in the extrnal classes,
    the ABAP statmetn 'ptortected section' is used to define declare the proccted section attributes


    the private section attributes can onl  be accessde in the same class.
    the private section attributes cannot be accessed in subclassed and external classes


    Different TYpes of attributes:
    Following are the different types of attributes.
    Instance Attributes
        Thes are exsted for each instance of a class.
        the instance attributes can be defined using normal ABAP statemetns ucch as dat, methosds etc
        The refernfce of aclasss can only be used to accesss the instacnce attribtes.
        The symbol instance connector '->' is used to access the instance atttribues.

        Syntax:
             CLASS< CLASS_NAME > DEFININTION.

             *Visibilty section
                Public Section
             *Define INstanceAttributes
                Data:<gv_var> TYPE <Dataelemnte/...>,


    Static Attributes: 
        They are existed only once nut can he used for nay number of instaces.
        The ABAP statemnt "CLAA--" is used to prefix to plain ABAP data declaretion definitoon stetments to defne static atttribues.
        The clss naem shoud only be usd to accss the static attributes but not clss refernce.
        The static attribues connecto symbol(===>) is used to refer the static attributes.

    

    Syntax:
        Define static sttribues
        data-data:<gv_static>...
        class-methods:<static_meth>...

        Aceess static attributes
            call methid < class_name>==><static_meth>

            HERE< class_name> is name.ss    