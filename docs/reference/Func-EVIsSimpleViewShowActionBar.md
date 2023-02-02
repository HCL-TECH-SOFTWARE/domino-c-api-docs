##### Function : Rich Text
##### EVIsSimpleViewShowActionBar - Returns TRUE if EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ACTION_BAR flag is set, FALSE otherwise.
---
##### #include <editods.h>
BOOL **EVIsSimpleViewShowActionBar(**

	CDEMBEDDEDVIEW *pEView);
**Description :**
To see if the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ACTION_BAR flag is set in the 
Flags member of the CDEMBEDDEDVIEW structure.  Implemented as a macro:

#define EVIsSimpleViewShowActionBar(pEView) ( (pEView)->Flags & 
EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ACTION_BAR )
**Parameters :**
Input :
pEView  -  Pointer to the CDEMBEDDEDVIEW structure.

Output :
(routine)  -  TRUE if EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_ACTION_BAR flag is set, FALSE otherwise.


**See Also :**
[CDEMBEDDEDVIEW](D:/md_files/CDEMBEDDEDVIEW.md)
[EMBEDDEDVIEW_FLAG_xxx](D:/md_files/EMBEDDEDVIEW_FLAG_xxx.md)
---
