##### Data Type : Rich Text
##### ACTIVEOBJECTSTORAGELINK - Active object storage specification.
---
##### #include <editods.h>
**Description :**
Java code used for active object hotspots is stored in $FILE items.  The file 
name for the $FILE item containing a class file is specified in this record.  
This record only appears following an ACTIVEOBJECT record, and is part of a 
CDHOTSPOTBEGIN record.  The fields of an ACTIVEOBJECTSTORAGELINK record are:

Length  Length of the file attachment name.
LinkType Reserved;  must be 0.
Reserved Reserved;  must be 0.

This record is followed by the name of the $FILE attachment, in LMBCS format 
with no NULL delimiter.
**See Also :**
[ACTIVEOBJECT](D:/md_files/ACTIVEOBJECT.md)
[CDHOTSPOTBEGIN](D:/md_files/CDHOTSPOTBEGIN.md)
---
