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
        METHODS <evnt_method> FOR EVENT < event_name> OF <class_name>.
            .
            .
        ENDCLASS.

