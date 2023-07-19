##### Data Type : Rich Text
##### HSOLERICHTEXT - OLE rich text hotspot record.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   WSIG  Header;       /* Signature and length of this record */
   DWORD Flags;        /* OLERT_FLAG_xxx flags */
   WORD  cFileObjName; /* Length of extendable $FILE object name
                          which contains object data */
   WORD  Reserved1;    /* Unused, must be 0 */
   WORD  Reserved2;    /* Unused, must be 0 */
   WORD  Reserved3;    /* Unused, must be 0 */
   DWORD Reserved4;    /* Unused, must be 0 */
/* The variable length portions go here in the following order:
         FileObjectName
*/
} HSOLERICHTEXT;

**Description :**

This record contains the name of the OLE object for this rich text hotspot.  This record is stored following the CDHOTSPOTBEGIN record for hotspots of type HOTSPOTREC_TYPE_OLERICHTEXT.  The length of this record is included in the length field of the CDHOTSPOTBEGIN record.  The fields in this record are:
<ul><br>

<ul>Header		Contains the record length; the signature byte is unused.<br>
Flags		Flags for this record;  see OLERT_FLAG_xxx for flag values.<br>
cFileObjName	Length, in bytes, of the file object name.<br>
Reserved1	Reserved;  must be 0.<br>
Reserved2	Reserved;  must be 0.<br>
Reserved3	Reserved;  must be 0.<br>
Reserved4	Reserved;  must be 0.</ul>
<br>
This record is followed by the file object name string.</ul>



**See Also :**
[CDHOTSPOTBEGIN](/domino-c-api-docs/reference/Data/CDHOTSPOTBEGIN)
[OLERT_FLAG_xxx](/domino-c-api-docs/reference/Symb/OLERT_FLAG_xxx)
[CDOLEOBJ_INFO](/domino-c-api-docs/reference/Data/CDOLEOBJ_INFO)
---
