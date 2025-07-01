Constructor and Class_constructor:
    They are the special methods and named as CONSTRUCTOR (instance) and CLASS_CONSTRUCTOR(Static).
    Constructor are called at run time automatically while creating an object.
    The constructors should be defined under PUBLIC SECTION only.
    The instance constructor can hav only Importing and Exceptions but not Exporting parameter.
    The static constructor cannot have any Importing and Exception parameters.
    Syntax:
        *Instace constuctor
       
        METHODS: CONSTRUCTOR IMPORTING....,
        *Static constructor
        CLASS_CONTRUCOTR,
        .
        .
        .


EVENTS IN OOABAP:
    Event in OOABAP is used to raise the messaage by an object.
    The ABAP statment "Events" is used to dfine the events.
    The ABAP statemets "RAISE" is used to raise an event.

    SYNTAX:
        CLASS<class_name>DEFINITION.
        ..
        EVENTS:<event_name>.
        ENDCLASS.
        ..
        .
        IF SY-SUBRC NE 0.

        * Raise Event.
            Raise<Event_name>.
        
        ENDIF.


EVENT HANDLER:
    It is used to call method of one class in another class to make use of same funtionlity.
    The additional statemetn "  FOR EVENT" is used to define the methods with event.
    The ABAP statement "SET HANDLER" is used to access attributes of event handler.

    Syntax:
        CLASS<cl_event_handler> DEFINITION.
        PUBLIC SECTION.
        METHODS <event_method> FOR EVENT < event_name> OF <class_name>.
            .
            .
        ENDCLASS.
        .

        *IMPLEMENT <cl_event_handler>.
        CLASS<cl_event_handler>IMPLEMENTATION.
        METHOD<event_handler>.
        *Bussiness logic
        -----------------
        ------------------
        ENDMETHOD.
        ENDCLASS.
        

        *Call event handler methods
        SET HANDLER <ref_event>---><event_method> FOR <ref_class_name>.




-----------------------------------------
-----------------------------------------------------------------------------
-----------------------------------------------------------------------------

***System variable in SAP ABAP.
They are predefined variables that automatically store system-related infromation during program execution.

They are not declared by the user but are accessible to all ABAP programs.

These variables provide details about the current system state, user context, and program excecution.

List of System variables:
    SY-CPAGE - Holds Current Page Number
    SY-CPROG - Contains Program Name
    SY-CUCOL - Cursor Position (Column)
    SY-CUROW - Cursor Position (Line)
    SY-DATLO - Local Date for User
    SY-DATUM - System Date
    SY-DATUD - Global Date Related TO UTC (GMT)
    SY-DBCNT - Number of entries read by DB Operation
    SY-DBNAM - Logical DB for ABAP/4 Program
    SY-DBSYS - System DB System
    SY-DYNNR - Number of Current Screen
    SY-INDEX - Number of Loop Passes
    SY-LANGu - SAP Log on Language Key
    SY-LILLI - Number of Current List Line
    SY-LINCT - Number of List Line
    SY-LINNO - Current line list creation
    SY-LINSz - Line Size of List
    SY-LISEL - Selected Line For interactive List
    SY-LSIND - Number of Secondary List
    SY-MANDT - Client Number FOR SAP Log On
    SY-MSGID - Message ID
    SY-MSGTY - Message Type
    SY-MSGNO - Message Number
    SY-MSGV1 - Message Variable1
    SY-MSGV2 - Message Variable2
    SY-MSGV3 - Message Variable3
    SY-MSGV4 - Message Variable4
    SY-OPSYS - Operating Sytem
    SY-PAART - Print Format
    SY-PAGCT - Page Size of List in Report Program
    SY-PAGNO - Current Page in the List
    SY-PDEST - Print Output Device
    SY-PFKEY - Run Time Current F key Status
    SY-REPID - Report Name in ABAP
    SY-SAPRL - SAP Release
    SY-SUBRC - Return Value after specific ABAP Statement
    SY-SYSID - SAP system ID
    SY-TABIX - Current line of Internal Table
    SY-TCODE - Current Transaction Code
    SY-TIMLO - Local Time of User
    SY-TITLE - Title of ABAP Program
    SY-TMAXL - Maximum entries in a Internal Table
    SY-TNAME - Name of INternal Table after first Access
    SY-UCOMM - Interact: Command field Function entry/Function code.
    SY-ULINE - Underline
    SY-UNAME - SessionL SAP user from Log On
    SY-UZEIT - System Time
    SY-VLINE - Vertical Bar

TRY...CATCH... Statements:
    This statements are used to try the specified bussiness logic (or) methods and catch the specified messages in case of fail.

    SYNTAX:
        TRY
        CALL METHOD...............

        CATCH <message>.
            .
            .
        ENDTRY.








Normal Method
It can declaer any of section(Public, Protected, Private)
It should call explicitly
It can any number of times by using the same object
It can contain any type of paremets (import, export , changing, returning)
Can return any numbers of values


Consturctor
It can declare in only public section
Automatically it will call. Explicall call not required
Instance Constructor will call in life time of object. Static Construtor will calll in life time of class
Instace constructor will allow only improt parameter, static contrucotrs will not allow any patamters
Never written any value(exporting value)



Inheritance
It is aprocess of using the propertises of one class inside other clas
The main aim of inheritace is trusablity of the omonets i.e. a componetn declared in oene class is accesssinleinside other lass,
I inheritance, two classes are involved (superclass, base class and sub class/ derived class).
The class which gives peropetis is called as super class/ base class
The class which takes the peroteis is called as sub-class/devied class.
Only Public and protesd componets can be inherited i.e. private componets cannot be inherited.



