##### Function : Rich Text
##### EVIsSimpleViewShowOnlySummarized - Returns TRUE if EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ONLY_SUMMARIZED flag is set, FALSE otherwise.

---
```
#include <editods.h>
BOOL EVIsSimpleViewShowOnlySummarized(

	CDEMBEDDEDVIEW *pEView);
```
**Description :**

To see if the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ONLY_SUMMARIZED ("summarize 
calendar entries") flag is set in the Flags member of the CDEMBEDDEDVIEW 
structure.  Implemented as a macro:

#define EVIsSimpleViewShowOnlySummarized(pEView) ( (pEView)->Flags & 
EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ONLY_SUMMARIZED)

**Parameters :**
Input :
pEView  -  Pointer to the CDEMBEDDEDVIEW structure.

Output :
(routine)  -  TRUE if EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ONLY_SUMMARIZED flag is set, FALSE otherwise.



**See Also :**
[CDEMBEDDEDVIEW](/reference/Data/CDEMBEDDEDVIEW)
[EMBEDDEDVIEW_FLAG_xxx](/reference/Symb/EMBEDDEDVIEW_FLAG_xxx)
---
