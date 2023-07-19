##### Data Type : Composite Data
##### CDMAPELEMENT - Structure defining a MAP element.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
 WSIG  Header;
   DWORD Flags;               /* reserved for future use */
   WORD  MapNameLength;       /* length of map name that follows */
   WORD  LastDefaultRegionID; /* last number used in auto
                                 generating default region names */
   WORD  LastRectRegionID;    /* last number used in auto
                                 generating rect names */
   WORD  LastCircleRegionID;  /* last number used in auto
                                 generating circle names */
   WORD  LastPolyRegionID;    /* last number used in auto
                                 generating polygon names */
   BYTE  Reserved[16];
/* variable part of map element follows:
 * MapName (string, not  null terminated)
 */
} CDMAPELEMENT;

**Description :**

Part of a client side image MAP which describes each region in an image and indicates the location of the document to be retrieved when the defined area is activated..
<ul><br>
<br>
Header	<br>
Flags			Reserved for future use.<br>
MapNameLength		Map Name Length.<br>
LastDefaultRegionID	Last number used in automatically generating default region names.<br>
LastRectRegionID		Last number used in automatically generating default rectangle names.<br>
LastCircleRegionID		Last number used in automatically generating circle names.<br>
LastPolyRegionID		Last number used in automatically generating polygon names.<br>
Reserved[16]<br>
<br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record sturctures such as this when accessing rich text item data in a note.</ul>



**See Also :**
[CDAREAELEMENT](/domino-c-api-docs/reference/Data/CDAREAELEMENT)
[CDBEGINRECORD](/domino-c-api-docs/reference/Data/CDBEGINRECORD)
[CDENDRECORD](/domino-c-api-docs/reference/Data/CDENDRECORD)
[CDEVENT](/domino-c-api-docs/reference/Data/CDEVENT)
[CDIDNAME](/domino-c-api-docs/reference/Data/CDIDNAME)
[CDMAPELEMENT_VERSIONxxx](/domino-c-api-docs/reference/Symb/CDMAPELEMENT_VERSIONxxx)
---
