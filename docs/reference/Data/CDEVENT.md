##### Data Type : Composite Data
##### CDEVENT - Structure which defines simple actions, fromulas or LotusScript for an image map..
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   WSIG  Header;
   DWORD Flags;
   WORD  EventType;       /* one of HTML_EVENT_xxx */
   WORD  ActionType;      /* one of ACTION_TYPE_xxx */
   DWORD ActionLength;    /* length of actions that follows */
	WORD SignatureLength; /* length of signature, if any */
   BYTE  Reserved[14];
/* Action follows here */
/* Signature follows here */
} CDEVENT;

**Description :**

This CD structure defines simple actions, formulas or LotusScript within a given image map.
<ul><br>
<br>
Header		Signature defining CDEVENT.<br>
Flags		See EVENT_HAS_LIBRARIES.<br>
EventType		See HTML_EVENT_xxx and HTML_EVENT_CLIENT_xxx for values.<br>
ActionType		See ACTION_TYPE_xxx for values.<br>
ActionLength<br>
SignatureLength<br>
Reserved[14]<br>
<br>
<br>
If the <tt><b>ActionType</b></tt> is <tt><b>ACTION_TYPE_JAVASCRIPT</b></tt>, the ActionLength indicates the total length of the JavaScript code.  The CDEVENT record is followed by one or more CDBLOBPART records, each one of them is followed by a section of the JavaScript code.  Loop through all the CDBLOBPART records to read in the complete JavaScript code.</ul>



**See Also :**
[ACTION_TYPE_xxx](/domino-c-api-docs/reference/Symb/ACTION_TYPE_xxx)
[CDBLOBPART](/domino-c-api-docs/reference/Data/CDBLOBPART)
[EVENT_HAS_LIBRARIES](/domino-c-api-docs/reference/Symb/EVENT_HAS_LIBRARIES)
[HTML_EVENT_CLIENT_xxx](/domino-c-api-docs/reference/Symb/HTML_EVENT_CLIENT_xxx)
[HTML_EVENT_xxx](/domino-c-api-docs/reference/Symb/HTML_EVENT_xxx)
---
