##### Function : Rich Text
##### EVSetSimpleViewHeaderOff - Sets the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_HEADER_OFF flag.
---
```
#include <editods.h>
void EVSetSimpleViewHeaderOff(

	CDEMBEDDEDVIEW *pEView,
	BOOL  fSet);
```
**Description :**

To set the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_HEADER_OFF flag on or off in the Flags 
member of the CDEMBEDDEDVIEW structure.  Implemented as a macro:

#define EVSetSimpleViewHeaderOff(pEView,fSet) \
{\
 if ( fSet ) (pEView)->Flags |= EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_HEADER_OFF;\
 else  (pEView)->Flags &= EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_HEADER_OFF;\
}

**Parameters :**
Input :
pEView  -  Pointer to the CDEMBEDDEDVIEW structure.

fSet  -  TRUE to set the EMBEDDEDVIEW_FLAG_SIMPLE_MOUSE_TRACK_ON flag on.  FALSE  to set the EMBEDDEDVIEW_FLAG_SIMPLE_MOUSE_TRACK_ON flag off.



**See Also :**
[CDEMBEDDEDVIEW](/reference/Data/CDEMBEDDEDVIEW)
[EMBEDDEDVIEW_FLAG_xxx](/reference/Symb/EMBEDDEDVIEW_FLAG_xxx)
---
