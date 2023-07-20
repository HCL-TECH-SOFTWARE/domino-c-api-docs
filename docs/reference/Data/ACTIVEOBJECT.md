##### Data Type : Rich Text
##### ACTIVEOBJECT - Hotspot active object record.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WORD  Version;          /* Version number */
   WORD  ObjectType;       /* Type of active object */
   DWORD Flags;            /* Flags */
   BYTE  WidthUnitType;    /* Currently only
                              ACTIVEOBJECT_UNIT_PIXELS and
                              ACTIVEOBJECT_UNIT_PERCENT supported */
   BYTE  HeightUnitType;   /* Currently only
                              ACTIVEOBJECT_UNIT_PIXELS and
                              ACTIVEOBJECT_UNIT_PERCENT supported */
   DWORD Width;            /* Width of active object */
   DWORD Height;           /* Height of active object */
   WORD  SpaceUnitType;    /* Currently  not used */
   WORD  HSpace;           /* Currently not used */
   WORD  VSpace;           /* Currently not used */
   WORD  DocURLNameLength; /* Length of document URL string that follows */
   WORD  CodebaseLength; /* Length of codebase string that follows */
   WORD  CodeLength;  /* Length of code string that follows */
   WORD  ObjectNameLength; /* Length of object name string that follows */
   WORD  StorageLinkCount; /* Number of ACTIVEOBJECTSTORAGELINK
                              structures that follow */ 
   WORD  ParamCount;       /* Number of ACTIVEOBJECTPARAM
                              structures that follow */
   BYTE  Used[16];
/* Variable length data (strings not null-terminated) follows here:
 - Document URL string
 - Codebase string
 - Code string (SRC info for plugins)
 - Object name (for Java applets)
 - ACTIVEOBJECTPARAM info (should be ParamCount number of these -
   Plugin ATTRIBUTE info should be here).
 - ACTIVEOBJECTSTORAGELINK info (should be StorageLinkCount number
   of these). */
} ACTIVEOBJECT;
```

**Description :**

This record contains the active object information for an active object hotspot.  This record is stored following the CDHOTSPOTBEGIN record for hotspots of type HOTSPOTREC_TYPE_ACTIVEOBJECT.  The length of this record is included in the length field of the CDHOTSPOTBEGIN record.  The fields in this record are:
<ul><br>
<br>
Version	Version number for the ACTIVEOBJECT record;  see ACTIVEOBJECT_VERSIONxxx.<br>
ObjectType	Type of active object;  must be one of ACTIVEOBJECT_TYPE_xxx.<br>
Flags	Flags.<br>
UnitType	In Release 4.6, only ACTIVEOBJECT_UNIT_PIXELS is supported.<br>
Width	Width of the active object.<br>
Height	Height of the active object.<br>
SpaceUnitType	Reserved;  must be 0.<br>
HSpace	Reserved;  must be 0.<br>
VSpace	Reserved;  must be 0.<br>
DocURLNameLength	Length of document URL string.<br>
CodebaseLength	Length of codebase string.<br>
CodeLength	Length of code string.<br>
ObjectNameLength	Length of the object name string.<br>
StorageLinkCount	Number of ACTIVEOBJECTSTORAGELINK records.<br>
ParamCount	Number of ACTIVEOBJECTPARAM records.<br>
Used	 <br>
<br>
This record is followed by the string values, in LMBCS format with no NULL delimiter:<br>
<br>
Document URL name.<br>
Codebase string.<br>
Code string (source information for plugins and Java).<br>
Object name (for OLE objects).<br>
<br>
Note that comments in editods.h indicate that the Object name is for Java applets.  This is incorrect.  The object name is for OLE objects.<br>
<br>
The ACTIVEOBJECTSTORAGELINK and ACTIVEOBJECTPARAM records follow the strings.</ul>



**See Also :**
[ACTIVEOBJECT_TYPE_xxx](/domino-c-api-docs/reference/Symb/ACTIVEOBJECT_TYPE_xxx)
[ACTIVEOBJECT_VERSIONxxx](/domino-c-api-docs/reference/Symb/ACTIVEOBJECT_VERSIONxxx)
[ACTIVEOBJECT_UNIT_xxx](/domino-c-api-docs/reference/Symb/ACTIVEOBJECT_UNIT_xxx)
[ACTIVEOBJECT_FLAG_xxx](/domino-c-api-docs/reference/Symb/ACTIVEOBJECT_FLAG_xxx)
[ACTIVEOBJECTPARAM](/domino-c-api-docs/reference/Data/ACTIVEOBJECTPARAM)
[ACTIVEOBJECTSTORAGELINK](/domino-c-api-docs/reference/Data/ACTIVEOBJECTSTORAGELINK)
---
