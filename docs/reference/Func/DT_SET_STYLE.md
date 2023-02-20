##### Function : Rich Text
##### DT_SET_STYLE - Stores the style value in DTFlags
---
```
#include <misc.h>
DWORD DT_SET_STYLE(

	DWORD  dwflag,
	BYTE  style);
```
**Description :**

This function stores the style value in DTFlags (See DT_XXX).

Implemented as a macro:

#define DT_SET_STYLE(dwflag, style) (dwflag = ((dwflag & 0xfff0ffff) | (style 
<< 0x10)))

**Parameters :**
Input :
dwflag  -  DTFlags.

style  -  The style value

Output :
(routine)  -  The DTFlags member of the CDEXT2FIELD structure that has a style set to the value specified in the "style" parameter.



**See Also :**
[CDEXT2FIELD](/reference/Data/CDEXT2FIELD)
[DT_xxx [CDEXT2FIELD - DTFlags]](/reference/Symb/DT_xxx [CDEXT2FIELD - DTFlags])
---
