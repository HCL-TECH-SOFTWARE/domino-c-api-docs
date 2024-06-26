##### Data Type : Composite Data
##### CDOLERTMARKER - OLE update version marker.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG  Header; /* Signature and length of this record */
   DWORD Flags;  /* (reserved) */
} CDOLERTMARKER;
```

**Description :**

This record is simply a marker in an OLE rich text hot spot that indicates that an OLE object with an associated rich text field (a $OLEObjRichTextField item) was updated by Release 4.6 or later of Domino or Notes.  If the OLE object is opened by an earlier release of Domino or Notes, this record will be ignored (like any other unrecognized CD record).  If this OLE object is updated from the rich text field by a release of Domino or Notes prior to 4.6, this record will not appear.
<ul><br>
<br>
If this record is present and the OLE object is updated from the rich text field by Release 4.6 or later of Domino or Notes, the object will not be updated if the rich text field is older than the contents of the OLE object.  If the rich text field is newer, the object is updated and a CDOLERTMARKER record is written.<br>
<br>
The fields in this record are:<br>

<ul>Header		Identifies this as a CDOLERTMARKER record.<br>
Flags		Reserved;  must be 0.</ul>
</ul>



**See Also :**
---
