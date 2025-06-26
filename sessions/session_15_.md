FS for develop ALV report: Display the data of ----------- purchase details for company based on purchase doc number.

---------------|-----------------------------------------
developer name |
---------------|-----------------------------------------
function name  |
---------------|----------------------------------------
assign date    |
---------------|----------------------------------------
delivery date  |
---------------|---------------------------------------

Business requirement : display the purchase data based on purxschase number using ALV report.

tables: EKKO, EKPO.

OUTPUT FIelds:

EKPO-EBELN.
EKPO-EBELP.
EKPO-MATNR.
EKPO-WERKS.
EKPO-LGORT.
EKPO-INFNR.
EKPO-MENGE.
EKPO-PEINH.
EKPO-NETWR.
EKPO-BURKS.
EKPO-EKORG.
EKPO-EKGRP.

SELECTION-screenL EBELN FROM EKKO-EBELN. IT will be a renge input.

Logic:
FETCH DATA FROM EKKO FIELDS: EBELN BUKRS EKORG EKGRP BASED ON SELECTION SCREEN FIELD.

    fetch the fields EBELN , EBELP MATNR WERKS LGORT INFNR MANGE MEINS PEINH NETWR FROM EKPO DATA FROM EKPO PASS EBELN EKKO-EBELN.

    

TYPE-POOLS: slis. " For ALV functions

TABLES: ekko, ekpo.

" Header Data Structure - EKKO
TYPES: BEGIN OF str_ekko,
         ebeln TYPE ekko-ebeln,
         bukrs TYPE ekko-bukrs,
         ekorg TYPE ekko-ekorg,
         ekgrp TYPE ekko-ekgrp,
       END OF str_ekko.

" Item Data Structure - EKPO
TYPES: BEGIN OF str_ekpo,
         ebeln TYPE ekpo-ebeln,
         ebelp TYPE ekpo-ebelp,
         matnr TYPE ekpo-matnr,
         werks TYPE ekpo-werks,
         lgort TYPE ekpo-lgort,
         infnr TYPE ekpo-infnr,
         menge TYPE ekpo-menge,
         meins TYPE ekpo-meins,
         peinh TYPE ekpo-peinh,
         netwr TYPE ekpo-netwr,
       END OF str_ekpo.

" Final Display Structure
TYPES: BEGIN OF str_final,
         ebeln TYPE ekpo-ebeln,
         ebelp TYPE ekpo-ebelp,
         matnr TYPE ekpo-matnr,
         werks TYPE ekpo-werks,
         lgort TYPE ekpo-lgort,
         infnr TYPE ekpo-infnr,
         menge TYPE ekpo-menge,
         meins TYPE ekpo-meins,
         peinh TYPE ekpo-peinh,
         netwr TYPE ekpo-netwr,
         bukrs TYPE ekko-bukrs,
         ekorg TYPE ekko-ekorg,
         ekgrp TYPE ekko-ekgrp,
       END OF str_final.



DATA: it_ekko  TYPE TABLE OF str_ekko,
      wa_ekko  TYPE str_ekko,
      it_ekpo  TYPE TABLE OF str_ekpo,
      wa_ekpo  TYPE str_ekpo,
      it_final TYPE TABLE OF str_final,
      wa_final TYPE str_final.

DATA: it_fcat  TYPE slis_t_fieldcat_alv,
      wa_fcat  TYPE slis_fieldcat_alv,
      layout   TYPE slis_layout_alv.


SELECT-OPTIONS: s_ebeln FOR ekko-ebeln.





START-OF-SELECTION.

  " Step 1: Fetch header data
  SELECT ebeln bukrs ekorg ekgrp
    INTO TABLE it_ekko
    FROM ekko
    WHERE ebeln IN s_ebeln.

  " Step 2: Fetch item data
  IF it_ekko IS NOT INITIAL.
    SELECT ebeln ebelp matnr werks lgort infnr menge meins peinh netwr
      INTO TABLE it_ekpo
      FROM ekpo
      FOR ALL ENTRIES IN it_ekko
      WHERE ebeln = it_ekko-ebeln.
  ENDIF.






  " Step 3: Merge both
  LOOP AT it_ekpo INTO wa_ekpo.
    READ TABLE it_ekko INTO wa_ekko WITH KEY ebeln = wa_ekpo-ebeln.
    IF sy-subrc = 0.
      wa_final-ebeln = wa_ekpo-ebeln.
      wa_final-ebelp = wa_ekpo-ebelp.
      wa_final-matnr = wa_ekpo-matnr.
      wa_final-werks = wa_ekpo-werks.
      wa_final-lgort = wa_ekpo-lgort.
      wa_final-infnr = wa_ekpo-infnr.
      wa_final-menge = wa_ekpo-menge.
      wa_final-meins = wa_ekpo-meins.
      wa_final-peinh = wa_ekpo-peinh.
      wa_final-netwr = wa_ekpo-netwr.
      wa_final-bukrs = wa_ekko-bukrs.
      wa_final-ekorg = wa_ekko-ekorg.
      wa_final-ekgrp = wa_ekko-ekgrp.
      APPEND wa_final TO it_final.
    ENDIF.
  ENDLOOP.





" EBELN - Purchase Document Number
CLEAR wa_fcat.
wa_fcat-col_pos   = 1.
wa_fcat-fieldname = 'EBELN'.
wa_fcat-seltext_m = 'Purchase Doc No'.
APPEND wa_fcat TO it_fcat.

" EBELP - Item Number
CLEAR wa_fcat.
wa_fcat-col_pos   = 2.
wa_fcat-fieldname = 'EBELP'.
wa_fcat-seltext_m = 'Item No'.
APPEND wa_fcat TO it_fcat.

" MATNR - Material Number
CLEAR wa_fcat.
wa_fcat-col_pos   = 3.
wa_fcat-fieldname = 'MATNR'.
wa_fcat-seltext_m = 'Material No'.
APPEND wa_fcat TO it_fcat.

" WERKS - Plant
CLEAR wa_fcat.
wa_fcat-col_pos   = 4.
wa_fcat-fieldname = 'WERKS'.
wa_fcat-seltext_m = 'Plant'.
APPEND wa_fcat TO it_fcat.

" LGORT - Storage Location
CLEAR wa_fcat.
wa_fcat-col_pos   = 5.
wa_fcat-fieldname = 'LGORT'.
wa_fcat-seltext_m = 'Storage Loc'.
APPEND wa_fcat TO it_fcat.

" INFNR - Info Record
CLEAR wa_fcat.
wa_fcat-col_pos   = 6.
wa_fcat-fieldname = 'INFNR'.
wa_fcat-seltext_m = 'Info Record'.
APPEND wa_fcat TO it_fcat.

" MENGE - Quantity
CLEAR wa_fcat.
wa_fcat-col_pos   = 7.
wa_fcat-fieldname = 'MENGE'.
wa_fcat-seltext_m = 'Quantity'.
APPEND wa_fcat TO it_fcat.

" MEINS - Unit of Measure
CLEAR wa_fcat.
wa_fcat-col_pos   = 8.
wa_fcat-fieldname = 'MEINS'.
wa_fcat-seltext_m = 'Unit'.
APPEND wa_fcat TO it_fcat.

" PEINH - Price Unit
CLEAR wa_fcat.
wa_fcat-col_pos   = 9.
wa_fcat-fieldname = 'PEINH'.
wa_fcat-seltext_m = 'Price Unit'.
APPEND wa_fcat TO it_fcat.

" NETWR - Net Price
CLEAR wa_fcat.
wa_fcat-col_pos   = 10.
wa_fcat-fieldname = 'NETWR'.
wa_fcat-seltext_m = 'Net Price'.
APPEND wa_fcat TO it_fcat.

" BUKRS - Company Code
CLEAR wa_fcat.
wa_fcat-col_pos   = 11.
wa_fcat-fieldname = 'BUKRS'.
wa_fcat-seltext_m = 'Company Code'.
APPEND wa_fcat TO it_fcat.

" EKORG - Purchasing Org
CLEAR wa_fcat.
wa_fcat-col_pos   = 12.
wa_fcat-fieldname = 'EKORG'.
wa_fcat-seltext_m = 'Purch Org'.
APPEND wa_fcat TO it_fcat.

" EKGRP - Purchasing Group
CLEAR wa_fcat.
wa_fcat-col_pos   = 13.
wa_fcat-fieldname = 'EKGRP'.
wa_fcat-seltext_m = 'Purch Group'.
APPEND wa_fcat TO it_fcat.


layout-zebra = 'X'.  " Optional: for alternate row shading

CALL FUNCTION 'REUSE_ALV_GRID_DISPLAY'
  EXPORTING
    
    is_layout   = layout
    it_fieldcat = it_fcat
  TABLES
    t_outtab    = it_final