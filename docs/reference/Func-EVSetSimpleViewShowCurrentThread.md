##### Function : Rich Text
##### EVSetSimpleViewShowCurrentThread - Sets the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_CURRENT_THREAD flag.
---
##### #include <editods.h>
void **EVSetSimpleViewShowCurrentThread(**

	CDEMBEDDEDVIEW *pEView,
	BOOL  fSet);
**Description :**
To set the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_CURRENT_THREAD flag on or off in 
the Flags member of the CDEMBEDDEDVIEW structure.  Implemented as a macro:

#define EVSetSimpleViewShowCurrentThread(pEView,fSet) \
	{\
	 if ( fSet ) (pEView)->Flags |= 
EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_CURRENT_THREAD;\
	 else (pEView)->Flags &= 
~EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_CURRENT_THREAD;\
	}
**Parameters :**
Input :
pEView  -  Pointer to the CDEMBEDDEDVIEW structure.

fSet  -  TRUE to set the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_CURRENT_THREAD flag on.  FALSE  to set the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_CURRENT_THREAD flag off.


**See Also :**
[CDEMBEDDEDVIEW](D:/md_files/CDEMBEDDEDVIEW.md)
[EMBEDDEDVIEW_FLAG_xxx](D:/md_files/EMBEDDEDVIEW_FLAG_xxx.md)
---
