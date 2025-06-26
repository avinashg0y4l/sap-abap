## Day 14: Function Module Assignment

### 🎯 Goal:
Create an ABAP program that uses a standard SAP Function Module to process customer data.

### 🪜 Steps:

1. **Go to Transaction SE38**  
   - Create a new executable program (e.g., `ZFM_CUSTOMER_DEMO`).

2. **Declare Structure and Internal Table**
   - Create a structure with fields: `KUNNR`, `ORT01`, `LAND1`.
   - Declare an internal table and a work area of this structure type.

3. **Create Selection Screen**
   - Use `PARAMETERS` to take customer number (`KNA1-KUNNR`) as single input.

4. **Fetch Data from KNA1 Table**
   - Use `SELECT` to fetch customer data matching the input.

5. **Use a Function Module**
   - Use standard function module `CONVERSION_EXIT_ALPHA_OUTPUT` to remove leading zeros from `KUNNR`.

6. **Display Results**
   - Show the formatted customer data using `WRITE`.

7. **Activate and Execute the Program**
   - Test with real customer numbers from your SAP system.

Assignment:




## 💻 ABAP Program Code

```abap
REPORT zfm_customer_demo.

*--- Step 1: Define structure
TYPES: BEGIN OF ty_customer,
         kunnr TYPE kna1-kunnr,
         ort01 TYPE kna1-ort01,
         land1 TYPE kna1-land1,
       END OF ty_customer.

*--- Step 2: Internal table and work area
DATA: it_customer TYPE TABLE OF ty_customer,
      wa_customer TYPE ty_customer.

*--- Step 3: Selection screen
PARAMETERS: p_kunnr TYPE kna1-kunnr.

*--- Step 4: Fetch data from KNA1
START-OF-SELECTION.

  SELECT kunnr
         ort01
         land1
    INTO TABLE it_customer
    FROM kna1
    WHERE kunnr = p_kunnr.

  IF sy-subrc <> 0.
    WRITE: / 'No customer found.'.
    EXIT.
  ENDIF.

*--- Step 5: Loop and process data
  LOOP AT it_customer INTO wa_customer.

*--- Step 6: Use Function Module to remove leading zeros
    DATA(lv_kunnr_display) = wa_customer-kunnr.
    CALL FUNCTION 'CONVERSION_EXIT_ALPHA_OUTPUT'
      EXPORTING
        input  = wa_customer-kunnr
      IMPORTING
        output = lv_kunnr_display.

*--- Step 7: Display customer data
    WRITE: / 'Customer Number:', lv_kunnr_display,
           / 'City           :', wa_customer-ort01,
           / 'Country Code   :', wa_customer-land1,
           / '------------------------------'.

  ENDLOOP.
```
















  ###reports
  reports are used when we nee to display the bulk of ata systematc way.


  type of report

  classical report
  intercative report
  alv report
    normalalv
    alv block
    alv hier
    alv interactive


classical:
    1. tabels declaration.
    2. declare structure.
    3. declare internal tble and workareas.
    4. develop selection scree:
        selection-options: for rand input.
        paramer: single input.
    5. data fetch using select queris.
    6. use loop for internal table.
    7. read the remaining internal tables in side loop.
    8. again loop on internal table write the fields which you want to display.



interactive:
    1. table declaration.
    2. declare structure.
    3. declare internal tables and work area.
    4. develop selection screen:
        paramertes: for single input.
        select0option: for range input.
    5. 1st screen data fetch using select queries
    6. use loop on internal table.
    7. wrie the fiels which you want to deispaly on 1st screen.
    8. use event: ata selection screeen.
    9. fetch then data using select quertes.
    loop on internal table.
    11. wriet ethe fields 
    


alv:
    1. declare type gourp.
    2. declare sturcture, interal tables and work areas,
    3. declare field catog internal table and work ares.
    4. deveop selection screren as per requirement.
    5. declare subroutine.
    6.create subroutie and add code into it.
    7. using select quesries fetch data.

    8. use loop on one internal table.
    9. reead the reaining tables into looop.


fieldcatlog:
    - it is table used to store output field infromation.
    - it is concept used in ALV reports.

syntax for declare internal table for fieldcatlog in report.
    data: INTERNAL_TABEL_NAME TYPE STANDARD_TABEL_OF_FIELDCATLOG.

Example:
    DATA: LT_FCAT TYPE SLIS_T_FIELDCAT_ALV.


Systax for declare work area for fieldcatlog in report.
    data: work_area_name type standard_structure_of_fieldcatlog.

Example: WA_FCAT TYPE SLIS_FIELDCAT_ALV.


syntax for buiding fieldcatlog in reprt.
    work_area_name-col_pos = '1'.
    work_area_name-fieldname= 'standard_field_name'.
    work_area_name-tabname= 'internal_table_name'.
    append work area name to internal table name.
    clear: work area name.



Example:
    WA_FCAT-COL_POS='1'.
    WA_FCAT-FIELDNAME='MATNR'.
    WA_FCAT-TABNAME='IT_MARA'.
    APPEND WA_FCAT TO LT_FCAT.
