##### Symbolic Value : Constants
##### EXTENDEDPABFLAGS3 - Value for DWORD extension to CDPABDEFINITION
---
##### #include <editods.h>
**Description :**
This DWORD extends the CDPABDEFINITION structure. 

If the Flags2 member of CDPABDEFINITION is set to PABFLAG2_MORE_FLAGS, the 
CDPABDEFINITION may be followed by a DWORD extension. If the value of this 
DWORD extension is EXTENDEDPABFLAGS3, then a second DWORD extension may be 
present with a value of PABFLAG3_HIDE_EE. These DWORD extensions follow the six 
R5 margin extension WORDs, if they are present.
**See Also :**
[CDPABDEFINITION](D:/md_files/CDPABDEFINITION.md)
[PABFLAG3_xxx](D:/md_files/PABFLAG3_xxx.md)
---
