##### Function : Rich Text
##### EVIsSimpleViewMouseTrackOn - Returns TRUE if EMBEDDEDVIEW_FLAG_SIMPLE_MOUSE_TRACK_ON flag is set, FALSE otherwise.
---
```
#include <editods.h>
BOOL EVIsSimpleViewMouseTrackOn(

	CDEMBEDDEDVIEW *pEView);
```
**Description :**

To see if the EMBEDDEDVIEW_FLAG_SIMPLE_MOUSE_TRACK_ON flag is set in the Flags 
member of the CDEMBEDDEDVIEW structure.  Implemented as a macro:

#define EVIsSimpleViewMouseTrackOn(pEView) ( (pEView)->Flags & 
EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_MOUSE_TRACK_ON )

**Parameters :**
Input :
pEView  -  Pointer to the CDEMBEDDEDVIEW structure.

Output :
(routine)  -  TRUE if EMBEDDEDVIEW_FLAG_SIMPLE_MOUSE_TRACK_ON flag is set, FALSE otherwise.



**See Also :**
[CDEMBEDDEDVIEW](/reference/Data/CDEMBEDDEDVIEW)
[EMBEDDEDVIEW_FLAG_xxx](/reference/Symb/EMBEDDEDVIEW_FLAG_xxx)
---
