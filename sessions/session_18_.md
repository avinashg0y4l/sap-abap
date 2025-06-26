Q. Write an ABAP report that allows the user to select material numbers from the MARA table and display their basic details such as Material Number, Created By, Material Type, and Industry Sector. On double-clicking a material number from the output, display its descriptions from the MAKT table in a secondary list. Use event blocks like TOP-OF-PAGE, AT LINE-SELECTION, and SELECT-OPTIONS appropriately.

    TABLES: mara, makt.

    TYPES: BEGIN OF ts_mara,
             matnr TYPE mara-matnr,
             ernam TYPE mara-ernam,
             mtart TYPE mara-mtart,
             mbrsh TYPE mara-mbrsh,
           END OF ts_mara.

    TYPES: BEGIN OF ts_makt,
             matnr TYPE makt-matnr,
             spras TYPE makt-spras,
             maktx TYPE makt-maktx,
           END OF ts_makt.

    DATA: lt_data  TYPE TABLE OF ts_mara,
          gs_data  TYPE ts_mara,
          lt_data1 TYPE TABLE OF ts_makt,
          gs_data1 TYPE ts_makt,
          lv_data  TYPE matnr.

    SELECTION-SCREEN: BEGIN OF BLOCK a1 WITH FRAME TITLE TEXT-001.
      SELECT-OPTIONS: s_matnr FOR lv_data.
    SELECTION-SCREEN END OF BLOCK a1.

    START-OF-SELECTION.

      SELECT matnr ernam mtart mbrsh
        INTO TABLE lt_data
        FROM mara
        WHERE matnr IN s_matnr.

      LOOP AT lt_data INTO gs_data.
        WRITE: / gs_data-matnr, gs_data-ernam, gs_data-mtart, gs_data-mbrsh.
        HIDE: gs_data-matnr.
      ENDLOOP.

    * This triggers automatically before the first WRITE statement
    TOP-OF-PAGE.
      WRITE: / 'Material Master Report'.

      ULINE.

    AT LINE-SELECTION.

      CLEAR lt_data1.

      SELECT matnr spras maktx
        INTO TABLE lt_data1
        FROM makt
        WHERE matnr = gs_data-matnr.



      LOOP AT lt_data1 INTO gs_data1.
        WRITE: / gs_data1-matnr, 10 gs_data1-spras, 20 gs_data1-maktx.
      ENDLOOP.
       TOP-OF-PAGE DURING LINE-SELECTION.
      WRITE: / 'Material Descriptions for:', gs_data-matnr.
      ULINE.







ALV_BLOCK REPORT:
    THIS FUNCTUIN MODULE IS USED TO DISPLAY MORE THAN ONE INTERNAL TABLE DATA ONTO ALV BLOCK LIST.
REUSE_ALV_BLOCK_LIST_INIT:
    THIS FUNCTION MODULE IS USED TO INITIALIZE THE ALV BOCK LIST.
REUSE_ALV_BLOCK_LIST_APPEND.
    THIS FUNCTION MODULE IS USED TO APPEND THE INTERNAL TABLE IT_EKKO TO ALV BLOCK LIST.
REUSE_ALV_BLOCK_LIST_APPEND.
    THIS FUNCTION MODULE IS USED TO APPEND THE INTERNAL TABLE IT_EKPO TO ALV BLOCK LIST.
REUSE_ALV_BLOCK_LIST_DISPLAY
    THIS FUNCTION MODULE IS USED TO DISPLAY ALV BLOCK LIST.


IMPORTING PARAMETERS
    PARAMETER NAME      TYPE     ASSOCIATED TYPE   DEFAULT VALUE ->  SHORT TEXT
    IS_LAYOUT           TYPE     SLIS_LAYOUT_ALV                     LIST LAYOUT SPECIFICATIONS
    IS_EVENTS           TYPE     SLIS_T_EVENT                        TBALE OF EVENTS TO PERFORMS
    IT_FIELDCAT         TYPE     SLIS_T_FIELDCAT_ALV                 FIELD CATALOG 
    I_TABNAME           TYPE     SLIS_TABNAME                        NAME OF INTERNAL OUTPUT TABLE
    I_TEXT              TYPE     SLIS_TEXT40       SPACE             TEXT OF THIS LIST FOR OVERVIEW SCREEN


TABLE PAREMETES
    PARAMETER NAME      TYPE        ASSICIATED TYPE         DEFAULT VALUE       SHORT TEXT
    T_OUTTAB            LIKE                                                    TABLE WITH DATA TO BE DISPLAYD





CREATE ZTABLE WITH FOLLOWING FIELDS.
NAME: ZTAB_STUDENTS
FIELDS: STU_NO, STU_NAME, GRADE.S


CREATE ANY 5 ENTRIES FOR : ZTAB_STUDENTS

CREATE DOMAIN FOR STUD_GRADE FIELD.


WRITE A PROGRAM FOR DISPLAY ANY 5 FIELD FROM KNA1 TABLES BASED OF KUNNR
PROGRAM NAME:ZCUST_DETAILS05.

create c  ZTT_WAREHOUSE06

create cutom tcode for zmaterial details01 program.