##### Data Type : Rich Text
##### HSOLERICHTEXT - OLE rich text hotspot record.
---
##### #include <editods.h>
**Description :**
This record contains the name of the OLE object for this rich text hotspot.  
This record is stored following the CDHOTSPOTBEGIN record for hotspots of type 
HOTSPOTREC_TYPE_OLERICHTEXT.  The length of this record is included in the 
length field of the CDHOTSPOTBEGIN record.  The fields in this record are:

Header  Contains the record length; the signature byte is unused.
Flags  Flags for this record;  see OLERT_FLAG_xxx for flag values.
cFileObjName Length, in bytes, of the file object name.
Reserved1 Reserved;  must be 0.
Reserved2 Reserved;  must be 0.
Reserved3 Reserved;  must be 0.
Reserved4 Reserved;  must be 0.

This record is followed by the file object name string.
**See Also :**
[CDHOTSPOTBEGIN](D:/md_files/CDHOTSPOTBEGIN.md)
[OLERT_FLAG_xxx](D:/md_files/OLERT_FLAG_xxx.md)
[CDOLEOBJ_INFO](D:/md_files/CDOLEOBJ_INFO.md)
---
