##### Function : Time
##### TimeConstant - Sets a TIMEDATE value to one of a set of known constants.
---
```
#include <misc.h>
void LNPUBLIC TimeConstant(

	WORD  TimeConstantType,
	TIMEDATE far *tdptr);
```
**Description :**

This function sets a given TIMEDATE value to one of the following constants:  
minimum value, maximum value, or wildcard (ANYDAY/ALLDAY).  See Symbolic Value, 
TIMEDATE_xxx.

**Parameters :**
Input :
TimeConstantType  -  A TIMEDATE constant.  See Symbolic Value, TIMEDATE_xxx.

Output :
(routine)  -  None


tdptr  -  Pointer to the returned TIMEDATE value.


**See Also :**
[TIMEDATE](/reference/Data/TIMEDATE)
[TIMEDATE_xxx](/reference/Symb/TIMEDATE_xxx)
---
