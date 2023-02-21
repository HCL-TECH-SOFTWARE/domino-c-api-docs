##### Function : Rich Text
##### EVIsSimpleViewShowSelectionMargin - Returns TRUE if EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_SELECTION_MARGIN flag is set, FALSE otherwise.
---
```
#include <editods.h>
BOOL EVIsSimpleViewShowSelectionMargin(

	CDEMBEDDEDVIEW *pEView);
```
**Description :**

To see if the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_SELECTION_MARGIN flag is set 
in the Flags member of the CDEMBEDDEDVIEW structure.  Implemented as a macro:

#define EVIsSimpleViewShowSelectionMargin(pEView) ( (pEView)->Flags & 
EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_SELECTION_MARGIN )

**Parameters :**
Input :
pEView  -  Pointer to the CDEMBEDDEDVIEW structure.

Output :
(routine)  -  TRUE if EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_SELECTION_MARGIN flag is set, FALSE otherwise.



**See Also :**
[CDEMBEDDEDVIEW](/domino-c-api-docs/reference/Data/CDEMBEDDEDVIEW)
[EMBEDDEDVIEW_FLAG_xxx](/domino-c-api-docs/reference/Symb/EMBEDDEDVIEW_FLAG_xxx)
---
