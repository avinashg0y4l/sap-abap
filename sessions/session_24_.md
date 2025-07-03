association view

enhancement in cds view

Access Control
    Annotation in Access controls
        @EndUserText.label:
        @MappingRoles

Understanding CDS Table Functions

    AMDP: ABAP Manage Database Procedures
        
        ABAP class -> AMDP Class 
                                    


        Class definition
            interfaces: if_amdp_marker_hdb.
         End of class



         Class implementation
            me
         end of class implementaion



cl_salv_table => factory


ABAP Managed Database Procedure (AMDP)
--------------------------------------

### What is a Database Procedure?

Database procedures are used to:

- Move database-intensive logic into the database.
- Minimize data transfer between the database and the application.
- Provide solutions when other modeling objects are not sufficient.

### Use Cases for Database Procedures

- Complex calculations.
- Imperative logic.
- Returning multiple datasets.
- Parallel processing.

### Developing Database Procedures and Limitations

- **SQLScript**: HANA-specific programming language for writing procedures.
- Procedures are created in the HANA Modeler perspective or HANA development perspective.
- HANA container and delivery unit are required to transport the procedures.
- Limitations may apply based on the database version and environment.
## What is AMDP (ABAP Managed Database Procedure)?

AMDP allows you to implement database procedures directly in ABAP classes using SQLScript or other supported database languages. These procedures are managed by the ABAP runtime and can be called like regular ABAP methods.

### Example: Simple AMDP Method

```abap
CLASS zcl_demo_amdp DEFINITION
    PUBLIC
    FINAL
    CREATE PUBLIC.

    PUBLIC SECTION.
        INTERFACES: if_amdp_marker_hdb.

        CLASS-METHODS get_data
            IMPORTING
                VALUE(iv_matnr) TYPE matnr
            EXPORTING
                VALUE(et_data) TYPE TABLE OF mara.
ENDCLASS.

CLASS zcl_demo_amdp IMPLEMENTATION.

    METHOD get_data BY DATABASE PROCEDURE
        FOR HDB
        LANGUAGE SQLSCRIPT
        OPTIONS READ-ONLY
        USING mara.

        et_data = SELECT * FROM mara WHERE matnr = :iv_matnr;

    ENDMETHOD.

ENDCLASS.
```

**Usage:**  
You can call `zcl_demo_amdp=>get_data` from your ABAP code to execute the database logic directly in HANA.
AMDP


