##### Function : Rich Text
##### EVSetSimpleViewShowSelectionMargin - Sets the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_SELECTION_MARGIN flag.
---
```
#include <editods.h>
void EVSetSimpleViewShowSelectionMargin(

	CDEMBEDDEDVIEW *pEView,
	BOOL  fSet);
```
**Description :**

To set the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_SELECTION_MARGIN flag on or off 
in the Flags member of the CDEMBEDDEDVIEW structure.  Implemented as a macro:

#define EVSetSimpleViewShowSelectionMargin(pEView,fSet) \
{\
 if ( fSet ) (pEView)->Flags |= 
EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_SELECTION_MARGIN;\
 else  (pEView)->Flags &= EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_SELECTION_MARGIN;\
}

**Parameters :**
Input :
pEView  -  Pointer to the CDEMBEDDEDVIEW structure.

fSet  -  TRUE to set the EMBEDDEDVIEW_FLAG_SIMPLE_MOUSE_TRACK_ON flag on.  FALSE  to set the EMBEDDEDVIEW_FLAG_SIMPLE_MOUSE_TRACK_ON flag off.



**See Also :**
[CDEMBEDDEDVIEW](/reference/Data/CDEMBEDDEDVIEW)
[EMBEDDEDVIEW_FLAG_xxx](/reference/Symb/EMBEDDEDVIEW_FLAG_xxx)
---
