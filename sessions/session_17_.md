OUTPUT function in ALV used: 'REUSE_ALV_GRID_DISPLAY'

Types of ALV report
    1. NORMAL ALVs
    2. ALV INTERACTIVE
    3. ALV HIERACHIACAL
    4. ALV BLOCK

EVENTS IN REPORTS:
    CLASSICAL REPORT:
        11 EVENTS.
            01.LOAD OF PROGRAM
            02.INITIALIZATION
            03.AT SELECTION SCREEN OUTPUT
            04.AT SELECTION SCREEN ON FIELD
            05.AT SELECTION SCREEN ON-VALUE REQUEST 
            06.AT SELECTION SCREEN ON-HELP REQUEST
            07.SELECTION SCREEN
            08.START OF SELECTION
            09.END OF SLECTION
            10.TOP-OF-PAGE
            11.END-OF-PAGE
        
    INTERACTIVE REPORT:
        4 EVENTS:
            01. AT LINE SELCTION.L
            02. AT USER COMMAND
            03. AT PF STATUS
            04. TOP-OF-PAGE-DURING LINE SELECTION



 01.LOAD OF PROGRAM
                THE LOAD OF PROGRAM EVENT LOADS THE PROGRAM INTO MEMORY FOR EXECUTION. ALWAYS, LOAD-OF-PROGRAM IS THE FIRST EVENT IN EXECUTION SEQUENCE.

                REPORT ZABAP_DATATYEPS.
                LOAD-OF-PROGRAM.
                TABLES: MARA.


            02.INITIALIZATION ()
                INITIALIZATION IS AN EVNET THAT IS USED FOR INITIALIZE VARIABLES, SCREEN VALES AND OTHE RDEFAULT ACTIONS.

        


