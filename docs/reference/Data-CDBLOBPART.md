##### Data Type : Composite Data
##### CDBLOBPART - Structure which defines a 'Binary Large Object'
---
##### #include <editods.h>
**Description :**
This CD record is used in conjunction with CD record CDEVENT.  If a CDEVENT 
record has an ActionType of ACTION_TYPE_JAVASCRIPT then CDBLOBPART contains the 
JavaScript code.  There may be more then one CDBLOBPART record for each 
CDEVENT.  Therefore it may be necessary to loop thorough all of the CDBLOBPART 
records to read in the complete JavaScript code.
**See Also :**
[CDEVENT](D:/md_files/CDEVENT.md)
---
