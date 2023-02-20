##### Function : Compound Text
##### CompoundTextInitStyle - Initializes a COMPOUNDSTYLE structure.
---
```
#include <easycd.h>
void LNPUBLIC CompoundTextInitStyle(

	COMPOUNDSTYLE far *pStyle);
```
**Description :**

This routine initializes a COMPOUNDSTYLE structure to the Domino default 
values.  A COMPOUNDSTYLE structure is very similar to a CDPABDEFINITION 
structure.

**Parameters :**

Output :
(routine)  -  None


pStyle  -  Pointer to a COMPOUNDSTYLE structure that will be initialized to Domino default values.


**Sample Usage :**
```
COMPOUNDSTYLE  Style;
...
CompoundTextInitStyle(&Style);
```
**See Also :**
[CompoundTextDefineStyle](/reference/Func/CompoundTextDefineStyle)
---
