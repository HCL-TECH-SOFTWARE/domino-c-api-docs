##### Function : Rich Text
##### EVSetSimpleViewShowAsWebLink - Sets the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_AS_WEB_LINK flag.
---
```
#include <editods.h>
void EVSetSimpleViewShowAsWebLink(

	CDEMBEDDEDVIEW *pEView,
	BOOL  fSet);
```
**Description :**

To set the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_AS_WEB_LINK flag on or off in the 
Flags member of the CDEMBEDDEDVIEW structure.  Implemented as a macro:

#define EVSetSimpleViewShowAsWebLink(pEView,fSet) \
{\
 if ( fSet ) (pEView)->Flags |= EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_AS_WEB_LINK;\
 else  (pEView)->Flags &= EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_AS_WEB_LINK;\
}

**Parameters :**
Input :
pEView  -  Pointer to the CDEMBEDDEDVIEW structure.

fSet  -  TRUE to set the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_AS_WEB_LINK flag on.  FALSE  to set the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_AS_WEB_LINK flag off.



**See Also :**
[CDEMBEDDEDVIEW](/reference/Data/CDEMBEDDEDVIEW)
[EMBEDDEDVIEW_FLAG_xxx](/reference/Symb/EMBEDDEDVIEW_FLAG_xxx)
---
