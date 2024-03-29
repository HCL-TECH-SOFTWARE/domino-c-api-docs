##### Function : Rich Text
##### DT_GET_STYLE - Retrieves the style value from DTFlags
---
```
#include <misc.h>
DWORD DT_GET_STYLE(

	DWORD  dwflag);
```
**Description :**

This function retrieves the style value from DTFlags (see DT_XXX). 

It is implemented as a macro:

#define DT_GET_STYLE(dwflag) ((dwflag & DT_STYLE_MSK) >> 0x10)

**Parameters :**
Input :
dwflag  -  DTFlag (see DT_XXX).

Output :
(routine)  -  The border type that is set in the DTFlags member of a CDEXT2FIELD structure.  See the DT_STYLE values in the DT_xxx [CDEXT2FIELD - DTFlags] symbolic for possible values.



**See Also :**
[CDEXT2FIELD](/domino-c-api-docs/reference/Data/CDEXT2FIELD)
[DT_xxx [CDEXT2FIELD - DTFlags]](/domino-c-api-docs/reference/Symb/DT_xxx [CDEXT2FIELD - DTFlags])
---
