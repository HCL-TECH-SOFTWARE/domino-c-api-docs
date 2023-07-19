##### Data Type : Composite Data
##### CDOLEOBJ_INFO - Specifies a connection to an OLE object.
---
```
#include <oleods.h>
```

**Definition :**

typedef struct {
   WSIG  Header;          /* Signature and length of this record */
   WORD  FileObjNameLength; /* Name of extendable $FILE object
                             containing object data */
   WORD  DescriptionNameLength; /* Length of object description */
   WORD  FieldNameLength; /* Length of field name in which object
                             resides */
   WORD  TextIndexObjNameLength; /* Name of the $FILE object
                             containing LMBCS text for object */
   OLE_GUID OleObjClass;  /* OLE ClassID GUID of OLE object */
   WORD  StorageFormat;   /* see OLE_STG_FMT_xxx */ 
   WORD  DisplayFormat;   /* see DDEFORMAT_xxx */
   DWORD Flags;           /* see OBJINFO_FLAGS_xxx */
   WORD  StorageFormatAppearedIn; /* Version # of Notes,
                             high byte=major, low byte=minor,
                             for display purposes */
   WORD  HTMLDataLength;  /* Length of HTML data for object */
   WORD  AssociatedFILEsLength;  /* Length of Associated $FILEs data for object 
*/
   WORD  Reserved3;       /* Unused, must be 0 */
   DWORD Reserved4;       /* Unused, must be 0 */
/* The variable length portions go here in the following order:
      FileObjectName
      DescriptionName
      Field Name in Document in which this object resides
      Full Text index $FILE object name
      HTML Data
	   Associated $FILEs Data
*/
} CDOLEOBJ_INFO;

**Description :**

This structure specifies a connection to an OLE object.


**See Also :**
[OLE_STG_FMT_xxx](/domino-c-api-docs/reference/Symb/OLE_STG_FMT_xxx)
[DDEFORMAT_xxx](/domino-c-api-docs/reference/Symb/DDEFORMAT_xxx)
[OBJINFO_FLAGS_xxx](/domino-c-api-docs/reference/Symb/OBJINFO_FLAGS_xxx)
---
