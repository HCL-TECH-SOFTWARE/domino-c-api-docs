##### Function : Rich Text
##### EVSetSimpleViewShowNewMailAtTop - Sets the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_NEWMAIL_AT_TOP flag.
---
##### #include <editods.h>
void **EVSetSimpleViewShowNewMailAtTop(**

	CDEMBEDDEDVIEW *pEView,
	BOOL  fSet);
**Description :**
To set the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_NEWMAIL_AT_TOP flag on or off in 
the Flags member of the CDEMBEDDEDVIEW structure.  Implemented as a macro:

#define EVSetSimpleViewShowNewMailAtTop(pEView,fSet) \
	{\
	 if ( fSet ) (pEView)->Flags |= 
EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_NEWMAIL_AT_TOP;\
	 else  (pEView)->Flags &= 
~EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_NEWMAIL_AT_TOP;\
	}
**Parameters :**
Input :
pEView  -  Pointer to the CDEMBEDDEDVIEW structure.

fSet  -  TRUE to set the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_NEWMAIL_AT_TOP flag on.  FALSE  to set the EMBEDDEDVIEW_FLAG_SIMPLE_VIEW_SHOW_NEWMAIL_AT_TOP flag off.


**See Also :**
[CDEMBEDDEDVIEW](D:/md_files/CDEMBEDDEDVIEW.md)
[EMBEDDEDVIEW_FLAG_xxx](D:/md_files/EMBEDDEDVIEW_FLAG_xxx.md)
---
