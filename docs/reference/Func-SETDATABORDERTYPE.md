##### Function : Rich Text
##### SETDATABORDERTYPE - Set the data border type bits stored in a Flags member of the CDDATAFLAGS structure.
---
##### #include <editods.h>
DWORD **SETDATABORDERTYPE(**

	DWORD  a,
	DWORD  b);
**Description :**
This macro sets the data border type bits of a Flags member of the CDDATAFLAGS 
structure and is defined as follows:

#define SETDATABORDERTYPE(a,b) a = ((DWORD)((a) & ~BARREC_DATA_BORDER_MASK) | 
                                   ((DWORD)(b - BAR_DATA_BORDER_OFFSET)))
**Parameters :**
Input :
a  -  A Flags member of the CDDATAFLAGS structure that is to have the data border type set.

b  -  The data border type value.  See the BARREC_DATA_BORDER_xxx symbolic for possible values.

Output :
(routine)  -  Flags member of the CDDATAFLAGS structure with the data border type set.


a  -  The Flags member of the CDDATAFLAGS structure that has the data border type set to the value specified in the b parameter.

**See Also :**
[BARREC_DATA_BORDER_xxx](D:/md_files/BARREC_DATA_BORDER_xxx.md)
[CDDATAFLAGS](D:/md_files/CDDATAFLAGS.md)
---
