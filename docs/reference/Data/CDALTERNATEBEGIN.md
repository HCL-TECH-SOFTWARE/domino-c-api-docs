##### Data Type : Composite Data
##### CDALTERNATEBEGIN - Start of alternate display records.
---
```
#include <editods.h>
```
**Description :**

Documents converted from HTML (Hyper-Text Markup Language), usually from a 
World Wide Web source, may contain "active object" instructions (such as a Java 
applet).  An active object may have an alternate representation which is to be 
displayed if the active object is not supported or is disabled.  When an active 
object is converted to a compound text representation, the alternate 
representation is stored beginning with a CDALTERNATEBEGIN record and ending 
with a CDALTERNATEEND record.  An alternate representation corresponds to the 
most recent active object with the same ACTIVEOBJECT_TYPE_xxx code, found in 
the Type field.  The fields in this record are:

Header Identifies this record as a CDALTERNATEBEGIN record
Type Type of active object for which this representation is an alternate (see 
ACTIVEOBJECT_TYPE_xxx)
SequenceNumber Sequence number for the active object for which this 
representation is an alternate
Flags Currently unused;  must be 0
DataLength Currently unused;  must be 0


**See Also :**
[CDALTERNATEEND](/reference/Data/CDALTERNATEEND)
[ACTIVEOBJECT_TYPE_xxx](/reference/Symb/ACTIVEOBJECT_TYPE_xxx)
---
