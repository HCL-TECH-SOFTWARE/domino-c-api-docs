##### Data Type : Composite Data
##### CDEVENTENTRY - Contains additional event information for Notes/Domino 6.
---
```
#include <editods.h>
```
**Description :**

Contains additional event information for Notes/Domino 6.

The fields in this structure are:

    Header - Signature and length of this record.
    
    wPlatform - Platform type (see PLATFORM_TYPE_xxx).

    wEventId - Event id:   HTML_EVENT_XXX, HTML_EVENT_CLIENT_XXX, . The event 
that this will run on... onClick, Exit, etc. 

    wActionType - Action type (the language... LotusScript, Javascript, 
Formula, etc.)
	Use the following enumerated data type for the values of the 
wActionType field:
	
typedef enum ACTION_TYPE
	{
	ACTION_FORMULA = 0,
	ACTION_CANNED_ACTION,
	ACTION_LOTUS_SCRIPT,
	ACTION_MISC,
	ACTION_COLLECTION_RULE,
	ACTION_JAVA_FILE,
	ACTION_JAVA,
	ACTION_JAVASCRIPT,
	ACTION_JAVASCRIPT_COMMON, // Use same javascript for both client and web
	ACTION_UNUSED,            // UNUSED
	ACTION_SECTION_EDIT,      // fullpack search on 12/10/00 showed no use 
of this
	ACTION_NULL, 
	ACTION_PROPERTIES,        // Obj properties (initially for OLE 
properties)
	ACTION_JSP,               // The code is jsp code
	ACTION_HTML,     // The code is HTML
	ACTION_MAX,               // The end of the 'real' types
	ACTION_OTHER = 98,
	ACTION_UNKNOWN
	} ACTION_TYPE;

    wReserved - Future use.

    dwReserved - Future use.

Note that CDEVENTENTRY records reside in items of type TYPE_COMPOSITE. 
Therefore, API programs that run on non-Intel architecture platforms must 
perform host/canonical conversion on structures of this type when accessing 
these records in an item in a note.

**See Also :**
[CDEVENT](/reference/Data/CDEVENT)
[HTML_EVENT_CLIENT_xxx](/reference/Symb/HTML_EVENT_CLIENT_xxx)
[HTML_EVENT_xxx](/reference/Symb/HTML_EVENT_xxx)
[PLATFORM_TYPE_xxx](/reference/Symb/PLATFORM_TYPE_xxx)
---
