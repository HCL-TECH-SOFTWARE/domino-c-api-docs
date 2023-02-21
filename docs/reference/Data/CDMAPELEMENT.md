##### Data Type : Composite Data
##### CDMAPELEMENT - Structure defining a MAP element.
---
```
#include <editods.h>
```
**Description :**

Part of a client side image MAP which describes each region in an image and 
indicates the location of the document to be retrieved when the defined area is 
activated..

Header 
Flags   Reserved for future use.
MapNameLength  Map Name Length.
LastDefaultRegionID Last number used in automatically generating default region 
names.
LastRectRegionID  Last number used in automatically generating default 
rectangle names.
LastCircleRegionID  Last number used in automatically generating circle names.
LastPolyRegionID  Last number used in automatically generating polygon names.
Reserved[16]


Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record sturctures such as this when accessing 
rich text item data in a note.

**See Also :**
[CDAREAELEMENT](/domino-c-api-docs/reference/Data/CDAREAELEMENT)
[CDBEGINRECORD](/domino-c-api-docs/reference/Data/CDBEGINRECORD)
[CDENDRECORD](/domino-c-api-docs/reference/Data/CDENDRECORD)
[CDEVENT](/domino-c-api-docs/reference/Data/CDEVENT)
[CDIDNAME](/domino-c-api-docs/reference/Data/CDIDNAME)
[CDMAPELEMENT_VERSIONxxx](/domino-c-api-docs/reference/Symb/CDMAPELEMENT_VERSIONxxx)
---
