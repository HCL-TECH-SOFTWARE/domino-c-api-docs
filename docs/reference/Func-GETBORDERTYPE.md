##### Function : Composite Data
##### GETBORDERTYPE - Return the border type value stored in the Flags member of a CDBAR structure.
---
##### #include <editods.h>
DWORD **GETBORDERTYPE(**

	DWORD  a);
**Description :**
This macro returns the border type value that is stored in the Flags member of 
the CDBAR structure and is defined as follows:

#define GETBORDERTYPE(a) ((DWORD)((a) & BARREC_BORDER_MASK) >> 28)

See the BARREC_BORDER values in the BARREC_xxx symbolic for possible return 
values.
**Parameters :**
Input :
a  -  The Flags member of the CDBAR structure.  This macro returns the border type that is stored in this DWORD.

Output :
(routine)  -  The border type that is set in the Flags member of a CDBAR structure.  See the BARREC_BORDER values in the BARREC_xxx symbolic for possible values.


**See Also :**
[CDBAR](D:/md_files/CDBAR.md)
[BARREC_xxx](D:/md_files/BARREC_xxx.md)
[SETBORDERTYPE](D:/md_files/SETBORDERTYPE.md)
---
