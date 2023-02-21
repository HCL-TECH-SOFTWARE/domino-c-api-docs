##### Function : Rich Text
##### EVSetSimpleViewShowActionBar - Sets the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ACTION_BAR flag.
---
```
#include <editods.h>
void EVSetSimpleViewShowActionBar(

	CDEMBEDDEDVIEW *pEView,
	BOOL  fSet);
```
**Description :**

To set the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ACTION_BAR flag on or off in the 
Flags member of the CDEMBEDDEDVIEW structure.  Implemented as a macro:

#define EVSetSimpleViewShowActionBar(pEView,fSet) \
{\
 if ( fSet ) (pEView)->Flags |= EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ACTION_BAR;\
 else  (pEView)->Flags &= EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ACTION_BAR;\
}

**Parameters :**
Input :
pEView  -  Pointer to the CDEMBEDDEDVIEW structure.

fSet  -  TRUE to set the EMBEDDEDVIEW_FLAG_SIMPLE_MOUSE_TRACK_ON flag on.  FALSE  to set the EMBEDDEDVIEW_FLAG_SIMPLE_MOUSE_TRACK_ON flag off.



**See Also :**
[CDEMBEDDEDVIEW](/domino-c-api-docs/reference/Data/CDEMBEDDEDVIEW)
[EMBEDDEDVIEW_FLAG_xxx](/domino-c-api-docs/reference/Symb/EMBEDDEDVIEW_FLAG_xxx)
---
