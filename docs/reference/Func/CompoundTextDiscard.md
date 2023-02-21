##### Function : Compound Text
##### CompoundTextDiscard - Discard a CompoundText context.
---
```
#include <easycd.h>
void LNPUBLIC CompoundTextDiscard(

	DHANDLE  hCompound);
```
**Description :**

This routine discards a CompoundText context and frees the resources allocated 
by the CompoundText context.  

Once a CompoundText context has been created, use this function in error 
processing.  Otherwise, use CompoundTextClose to close a CompoundText context 
and free the resources allocated by the CompoundText context.

**Parameters :**
Input :
hCompound  -  Handle of the CompoundText context to close and discard.

Output :
(routine)  -  None



**See Also :**
[CompoundTextClose](/domino-c-api-docs/reference/Func/CompoundTextClose)
---
