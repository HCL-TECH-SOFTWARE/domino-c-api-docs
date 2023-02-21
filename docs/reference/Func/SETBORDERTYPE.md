##### Function : Composite Data
##### SETBORDERTYPE - Set the border type bits in the Flags member of a CDBAR structure
---
```
#include <editods.h>
DWORD SETBORDERTYPE(

	DWORD  a,
	DWORD  b);
```
**Description :**

This macro sets the border type bits of the Flags member of the CDBAR structure 
and is defined as follows:

#define SETBORDERTYPE(a,b) a = ((DWORD)((a) & ~BARREC_BORDER_MASK) | 
((DWORD)(b) << 28))

**Parameters :**
Input :
a  -  The Flags member of the CDBAR structure that is to have the border type set.

b  -  The border type value.  See the BARREC_BORDER values in the BARREC_xxx symbolic for possible values.

Output :
(routine)  -  Flags member of the CDBAR structure with the border type set.


a  -  The Flags member of the CDBAR structure that has the border type set to the value specified in the b parameter.


**Sample Usage :**
```
SETBORDERTYPE(pcdBar.Flags, BARREC_BORDER_NONE);
```
**See Also :**
[CDBAR](/domino-c-api-docs/reference/Data/CDBAR)
[BARREC_xxx](/domino-c-api-docs/reference/Symb/BARREC_xxx)
[GETBORDERTYPE](/domino-c-api-docs/reference/Func/GETBORDERTYPE)
---
