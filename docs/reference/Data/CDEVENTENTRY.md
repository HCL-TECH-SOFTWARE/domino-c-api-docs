##### Data Type : Composite Data
##### CDEVENTENTRY - Contains additional event information for Notes/Domino 6.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
 WSIG Header;  /* Signature and length of this record */
 WORD wPlatform;  /* Platform type */
 WORD wEventId;  /* Event id. The event that this will run on... OnClick, Exit, 
etc. */
 WORD wActionType; /* Action type (the language... LotusScript, Javascript, 
Formula, etc. */
 WORD wReserved;  /* future use */
 DWORD dwReserved;  /* future use */
} CDEVENTENTRY;

**Description :**

Contains additional event information for Notes/Domino 6.
<ul><br>
<br>
The fields in this structure are:<br>
<br>
    Header - Signature and length of this record.<br>
    <br>
    wPlatform - Platform type (see PLATFORM_TYPE_xxx).<br>
<br>
    wEventId - Event id:   HTML_EVENT_XXX, HTML_EVENT_CLIENT_XXX, . The event that this will run on... onClick, Exit, etc. <br>
<br>
    wActionType - Action type (the language... LotusScript, Javascript, Formula, etc.)<br>
	Use the following enumerated data type for the values of the wActionType field:<br>
	</ul>
<font face="Courier">typedef enum ACTION_TYPE</font><br>
<font face="Courier">	{</font><br>
<font face="Courier">	ACTION_FORMULA = 0,</font><br>
<font face="Courier">	ACTION_CANNED_ACTION,</font><br>
<font face="Courier">	ACTION_LOTUS_SCRIPT,</font><br>
<font face="Courier">	ACTION_MISC,</font><br>
<font face="Courier">	ACTION_COLLECTION_RULE,</font><br>
<font face="Courier">	ACTION_JAVA_FILE,</font><br>
<font face="Courier">	ACTION_JAVA,</font><br>
<font face="Courier">	ACTION_JAVASCRIPT,</font><br>
<font face="Courier">	ACTION_JAVASCRIPT_COMMON, // Use same javascript for both client and web</font><br>
<font face="Courier">	ACTION_UNUSED,            // UNUSED</font><br>
<font face="Courier">	ACTION_SECTION_EDIT,      // fullpack search on 12/10/00 showed no use of this</font><br>
<font face="Courier">	ACTION_NULL, </font><br>
<font face="Courier">	ACTION_PROPERTIES,        // Obj properties (initially for OLE properties)</font><br>
<font face="Courier">	ACTION_JSP,               // The code is jsp code</font><br>
<font face="Courier">	ACTION_HTML,			  // The code is HTML</font><br>
<font face="Courier">	ACTION_MAX,               // The end of the 'real' types</font><br>
<font face="Courier">	ACTION_OTHER = 98,</font><br>
<font face="Courier">	ACTION_UNKNOWN</font><br>
<font face="Courier">	} ACTION_TYPE;</font>
<ul><br>
    wReserved - Future use.<br>
<br>
    dwReserved - Future use.<br>
<br>
Note that CDEVENTENTRY records reside in items of type TYPE_COMPOSITE. Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on structures of this type when accessing these records in an item in a note.</ul>



**See Also :**
[CDEVENT](/domino-c-api-docs/reference/Data/CDEVENT)
[HTML_EVENT_CLIENT_xxx](/domino-c-api-docs/reference/Symb/HTML_EVENT_CLIENT_xxx)
[HTML_EVENT_xxx](/domino-c-api-docs/reference/Symb/HTML_EVENT_xxx)
[PLATFORM_TYPE_xxx](/domino-c-api-docs/reference/Symb/PLATFORM_TYPE_xxx)
---
