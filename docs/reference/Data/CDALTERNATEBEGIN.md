##### Data Type : Composite Data
##### CDALTERNATEBEGIN - Start of alternate display records.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG  Header;         /* Signature and length of this record */
   WORD  Type;           /* Type of active object this is an 
                               alternate for */
   DWORD SequenceNumber; /* ID/Sequence number should match what's
                            in some ACTIVEOBJECT in the doc */
   DWORD Flags;          /* Unused; must be 0 */
   WORD  DataLength;     /* Unused; must be 0 */
/* Data Follows. */
} CDALTERNATEBEGIN;
```

**Description :**

Documents converted from HTML (Hyper-Text Markup Language), usually from a World Wide Web source, may contain &quot;active object&quot; instructions (such as a Java applet).  An active object may have an alternate representation which is to be displayed if the active object is not supported or is disabled.  When an active object is converted to a compound text representation, the alternate representation is stored beginning with a CDALTERNATEBEGIN record and ending with a CDALTERNATEEND record.  An alternate representation corresponds to the most recent active object with the same ACTIVEOBJECT_TYPE_xxx code, found in the Type field.  The fields in this record are:
<ul><br>

<ul>Header	Identifies this record as a CDALTERNATEBEGIN record<br>
Type	Type of active object for which this representation is an alternate (see ACTIVEOBJECT_TYPE_xxx)<br>
SequenceNumber	Sequence number for the active object for which this representation is an alternate<br>
Flags	Currently unused;  must be 0<br>
DataLength	Currently unused;  must be 0</ul>
</ul>



**See Also :**
[CDALTERNATEEND](/domino-c-api-docs/reference/Data/CDALTERNATEEND)
[ACTIVEOBJECT_TYPE_xxx](/domino-c-api-docs/reference/Symb/ACTIVEOBJECT_TYPE_xxx)
---
