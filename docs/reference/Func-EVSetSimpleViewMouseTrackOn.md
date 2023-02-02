##### Function : Rich Text
##### EVSetSimpleViewMouseTrackOn - Sets the EMBEDDEDVIEW_FLAG_SIMPLE_MOUSE_TRACK_ON flag.
---
##### #include <editods.h>
void **EVSetSimpleViewMouseTrackOn(**

	CDEMBEDDEDVIEW *pEView,
	BOOL  fSet);
**Description :**
To set the EMBEDDEDVIEW_FLAG_SIMPLE_MOUSE_TRACK_ON flag on or off in the Flags 
member of the CDEMBEDDEDVIEW structure.  Implemented as a macro:

#define EVSetSimpleViewMouseTrackOn(pEView,fSet) \
{\
 if ( fSet ) (pEView)->Flags |= EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_MOUSE_TRACK_ON;\
 else  (pEView)->Flags &= EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_MOUSE_TRACK_ON;\
}
**Parameters :**
Input :
pEView  -  Pointer to the CDEMBEDDEDVIEW structure.

fSet  -  TRUE to set the EMBEDDEDVIEW_FLAG_SIMPLE_MOUSE_TRACK_ON flag on.  FALSE  to set the EMBEDDEDVIEW_FLAG_SIMPLE_MOUSE_TRACK_ON flag off.


**See Also :**
[CDEMBEDDEDVIEW](D:/md_files/CDEMBEDDEDVIEW.md)
[EMBEDDEDVIEW_FLAG_xxx](D:/md_files/EMBEDDEDVIEW_FLAG_xxx.md)
---
