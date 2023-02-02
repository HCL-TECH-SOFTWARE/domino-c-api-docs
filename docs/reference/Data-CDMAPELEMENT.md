##### Data Type : Composite Data
##### CDMAPELEMENT - Structure defining a MAP element.
---
##### #include <editods.h>
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
[CDAREAELEMENT](D:/md_files/CDAREAELEMENT.md)
[CDBEGINRECORD](D:/md_files/CDBEGINRECORD.md)
[CDENDRECORD](D:/md_files/CDENDRECORD.md)
[CDEVENT](D:/md_files/CDEVENT.md)
[CDIDNAME](D:/md_files/CDIDNAME.md)
[CDMAPELEMENT_VERSIONxxx](D:/md_files/CDMAPELEMENT_VERSIONxxx.md)
---
