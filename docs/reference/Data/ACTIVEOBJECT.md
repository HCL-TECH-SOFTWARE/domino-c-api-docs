##### Data Type : Rich Text
##### ACTIVEOBJECT - Hotspot active object record.
---
```
#include <editods.h>
```
**Description :**

This record contains the active object information for an active object 
hotspot.  This record is stored following the CDHOTSPOTBEGIN record for 
hotspots of type HOTSPOTREC_TYPE_ACTIVEOBJECT.  The length of this record is 
included in the length field of the CDHOTSPOTBEGIN record.  The fields in this 
record are:

Version Version number for the ACTIVEOBJECT record;  see 
ACTIVEOBJECT_VERSIONxxx.
ObjectType Type of active object;  must be one of ACTIVEOBJECT_TYPE_xxx.
Flags Flags.
UnitType In Release 4.6, only ACTIVEOBJECT_UNIT_PIXELS is supported.
Width Width of the active object.
Height Height of the active object.
SpaceUnitType Reserved;  must be 0.
HSpace Reserved;  must be 0.
VSpace Reserved;  must be 0.
DocURLNameLength Length of document URL string.
CodebaseLength Length of codebase string.
CodeLength Length of code string.
ObjectNameLength Length of the object name string.
StorageLinkCount Number of ACTIVEOBJECTSTORAGELINK records.
ParamCount Number of ACTIVEOBJECTPARAM records.
Used  

This record is followed by the string values, in LMBCS format with no NULL 
delimiter:

Document URL name.
Codebase string.
Code string (source information for plugins and Java).
Object name (for OLE objects).

Note that comments in editods.h indicate that the Object name is for Java 
applets.  This is incorrect.  The object name is for OLE objects.

The ACTIVEOBJECTSTORAGELINK and ACTIVEOBJECTPARAM records follow the strings.

**See Also :**
[ACTIVEOBJECT_TYPE_xxx](/reference/Symb/ACTIVEOBJECT_TYPE_xxx)
[ACTIVEOBJECT_VERSIONxxx](/reference/Symb/ACTIVEOBJECT_VERSIONxxx)
[ACTIVEOBJECT_UNIT_xxx](/reference/Symb/ACTIVEOBJECT_UNIT_xxx)
[ACTIVEOBJECT_FLAG_xxx](/reference/Symb/ACTIVEOBJECT_FLAG_xxx)
[ACTIVEOBJECTPARAM](/reference/Data/ACTIVEOBJECTPARAM)
[ACTIVEOBJECTSTORAGELINK](/reference/Data/ACTIVEOBJECTSTORAGELINK)
---
