



assignment 2.

create alv report for sales regtser data.

tables: vbak , vbap.

selection sceree fields: vbeln, vkorg both signle input.

output fields

VBAK:
    VBELN
    VTWEG
    SPART
    VKGRP
    VKBUR
    GSBER

VBAP:
    VBELN
    POSNR
    MATNR
    MATWA

LOGIC:
    FETCH DATA FROM VBAK FOR BELOW FIELDS
    VBELN
    POSNR
    MATNR
    MATWA BASED ON SELECTION SCREEN VBELN.

FETCH DATA FROM VBAP BELOW FIELDS:
    VBELN
    POSNR
    MATNR
    MATWA
    PASS VABK-VBELN TO VBAP-VEBLN.










CLEAR wa_fcat.
wa_fcat-col_pos   = 1.
wa_fcat-fieldname = 'VBELN'.
wa_fcat-seltext_m = 'Sales Doc No'.
APPEND wa_fcat TO it_fcat.

CLEAR wa_fcat.
wa_fcat-col_pos   = 2.
wa_fcat-fieldname = 'VTWEG'.
wa_fcat-seltext_m = 'Dist. Channel'.
APPEND wa_fcat TO it_fcat.

CLEAR wa_fcat.
wa_fcat-col_pos   = 3.
wa_fcat-fieldname = 'SPART'.
wa_fcat-seltext_m = 'Division'.
APPEND wa_fcat TO it_fcat.

CLEAR wa_fcat.
wa_fcat-col_pos   = 4.
wa_fcat-fieldname = 'VKGRP'.
wa_fcat-seltext_m = 'Sales Group'.
APPEND wa_fcat TO it_fcat.

CLEAR wa_fcat.
wa_fcat-col_pos   = 5.
wa_fcat-fieldname = 'VKBUR'.
wa_fcat-seltext_m = 'Sales Office'.
APPEND wa_fcat TO it_fcat.

CLEAR wa_fcat.
wa_fcat-col_pos   = 6.
wa_fcat-fieldname = 'GSBER'.
wa_fcat-seltext_m = 'Business Area'.
APPEND wa_fcat TO it_fcat.

CLEAR wa_fcat.
wa_fcat-col_pos   = 7.
wa_fcat-fieldname = 'POSNR'.
wa_fcat-seltext_m = 'Item No'.
APPEND wa_fcat TO it_fcat.

CLEAR wa_fcat.
wa_fcat-col_pos   = 8.
wa_fcat-fieldname = 'MATNR'.
wa_fcat-seltext_m = 'Material No'.
APPEND wa_fcat TO it_fcat.

CLEAR wa_fcat.
wa_fcat-col_pos   = 9.
wa_fcat-fieldname = 'MATWA'.
wa_fcat-seltext_m = 'Material Desc'.
APPEND wa_fcat TO it_fcat.
