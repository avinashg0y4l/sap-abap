AMDP Functions

Table Function

### What are AMDP, CDS, and CDS Table Functions?

**AMDP (ABAP Managed Database Procedures):**  
AMDP allows you to implement database procedures directly in ABAP classes using SQLScript or other supported languages. These procedures run directly in the HANA database for better performance, especially for complex data processing.

**CDS (Core Data Services):**  
CDS is a data modeling infrastructure in SAP that enables you to define semantically rich data models (views) on the database. CDS views are defined using the CDS language and can be used in ABAP programs, analytics, and UI applications.

**CDS Table Function:**  
A CDS Table Function is a special type of CDS view whose data is provided by an AMDP method. It allows you to define complex logic in the database (using SQLScript) and expose the result as a table-like structure in ABAP, combining the flexibility of AMDP with the modeling power of CDS.


Creating a CDS Table Function:
    Creating Data Definition for CDS Table Function
        -Use Template Define TableFunctionWithParamters
        -Define parameters (options) and return value(don't forget the cliednt field)
        -Leave the information after IMPLEMENTED BY as ist is (not checked by syntax check)
        -Avtivate the Data Definition
    
    Create AMDP Class With AMDP Method
        - Create a global class and implementd interface IF_AMDP_MARKER_HDB
        -Define a public static method with addition FOR TABLE FUNCTIONS...
        -Implement the method as an AMDP function.
        -Activate the global class
    
    Complete the Definition of the CDS Table Function
        -Enter th AMDP class AMDP method after IMPELEMENTED BY 
        -Activate the Data Definition
        -Test the CDS table function in data preview



### Difference between Table Function and AMDP

| Aspect                | Table Function (CDS Table Function)                                  | AMDP (ABAP Managed Database Procedure)                        |
|-----------------------|---------------------------------------------------------------------|---------------------------------------------------------------|
| Definition            | A CDS view whose data is provided by an AMDP method.                | Database procedures implemented in ABAP classes using SQLScript or other supported languages. |
| Usage                 | Used to expose complex logic as a table-like structure in ABAP.      | Used for complex data processing directly in the HANA database.|
| Implementation        | Defined in CDS with logic in an AMDP method.                        | Implemented as methods in ABAP classes with IF_AMDP_MARKER_HDB interface. |
| Return Type           | Always returns a table (tabular result).                            | Can return scalar values, tables, or perform actions.          |
| Integration           | Easily consumed in ABAP, analytics, and UI via CDS views.           | Called from ABAP programs or used as implementation for table functions. |
| Syntax                | Combination of CDS definition and AMDP method.                      | Purely ABAP class method with SQLScript code.                  |
| Performance           | Both run in the database for high performance.                      | Both optimized for HANA, but AMDP can be used standalone.      |






ALV with Integrated Data Access(IDA)
The ALV with intergrated data access(ALVIDA) is signifaclty different to the classical ALV - Espacially when used in combination with ABAP CDS.



ABAP