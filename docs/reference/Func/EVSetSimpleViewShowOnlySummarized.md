##### Function : Rich Text
##### EVSetSimpleViewShowOnlySummarized - Sets the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ONLY_SUMMARIZED flag.
---
```
#include <editods.h>
void EVSetSimpleViewShowOnlySummarized(

	CDEMBEDDEDVIEW *pEView,
	BOOL  fSet);
```
**Description :**

To set the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ONLY_SUMMARIZED flag on or off in 
the Flags member of the CDEMBEDDEDVIEW structure.  Implemented as a macro:

#define EVSetSimpleViewShowOnlySummarized(pEView,fSet) \
	{\
	 if ( fSet ) (pEView)->Flags |= 
EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ONLY_SUMMARIZED;\
	 else  (pEView)->Flags &= 
~EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ONLY_SUMMARIZED;\
	}

**Parameters :**
Input :
pEView  -  Pointer to the CDEMBEDDEDVIEW structure.

fSet  -  TRUE to set the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ONLY_SUMMARIZED flag on.  FALSE  to set the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ONLY_SUMMARIZED flag off.



**See Also :**
[CDEMBEDDEDVIEW](/reference/Data/CDEMBEDDEDVIEW)
[EMBEDDEDVIEW_FLAG_xxx](/reference/Symb/EMBEDDEDVIEW_FLAG_xxx)
---
