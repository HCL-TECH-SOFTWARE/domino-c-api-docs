##### Function : Rich Text
##### EVIsSimpleViewShowNewMailAtTop - Returns TRUE if EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_NEWMAIL_AT_TOP flag is set, FALSE otherwise.
---
```
#include <editods.h>
BOOL EVIsSimpleViewShowNewMailAtTop(

	CDEMBEDDEDVIEW *pEView);
```
**Description :**

To see if the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_NEWMAIL_AT_TOP ("show recent 
first") flag is set in the Flags member of the CDEMBEDDEDVIEW structure.  
Implemented as a macro:

#define EVIsSimpleViewShowNewMailAtTop(pEView) ( (pEView)->Flags & 
EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_NEWMAIL_AT_TOP)

**Parameters :**
Input :
pEView  -  Pointer to the CDEMBEDDEDVIEW structure.

Output :
(routine)  -  TRUE if EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_NEWMAIL_AT_TOP flag is set, FALSE otherwise.



**See Also :**
[CDEMBEDDEDVIEW](/reference/Data/CDEMBEDDEDVIEW)
[EMBEDDEDVIEW_FLAG_xxx](/reference/Symb/EMBEDDEDVIEW_FLAG_xxx)
---
