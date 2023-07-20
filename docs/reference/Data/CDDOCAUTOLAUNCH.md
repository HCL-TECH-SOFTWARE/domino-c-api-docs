##### Data Type : Composite Data
##### CDDOCAUTOLAUNCH - Format of an on-disk autolaunch item.
---
```
#include <oleods.h>
```

**Definition :**
```
typedef struct {
   WSIG  Header;           /* Signature and length of this rec */
   DWORD ObjectType;       /* Type of object to launch,
                              see AUTOLAUNCH_OBJTYPE_xxx */
   DWORD HideWhenFlags;    /* see HIDE_xxx */
   DWORD LaunchWhenFlags;  /* see LAUNCH_WHEN_xxx */
   DWORD OleFlags;         /* see OLE_xxx */
   DWORD CopyToFieldFlags; /* see FIELD_COPY_xxx */
   DWORD Spare1;
   DWORD Spare2;
   WORD  FieldNameLength;  /* If named field, field name length */
   OLE_GUID  OleObjClass;  /* ClassID GUID of OLE object, if create
                              new */
/* Field Name, if used, goes here */
} CDDOCAUTOLAUNCH;
```

**Description :**

Structure of an on-disk autolaunch item.  Most of the information contained in this structure refers to OLE autolaunching behaviors.


**See Also :**
[AUTOLAUNCH_OBJTYPE_xxx](/domino-c-api-docs/reference/Symb/AUTOLAUNCH_OBJTYPE_xxx)
[FIELD_COPY_xxx](/domino-c-api-docs/reference/Symb/FIELD_COPY_xxx)
[HIDE_xxx](/domino-c-api-docs/reference/Symb/HIDE_xxx)
[LAUNCH_WHEN_xxx](/domino-c-api-docs/reference/Symb/LAUNCH_WHEN_xxx)
[OLE_xxx](/domino-c-api-docs/reference/Symb/OLE_xxx)
---
