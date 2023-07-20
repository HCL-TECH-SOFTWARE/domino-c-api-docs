##### Data Type : Composite Data
##### CDOLEBEGIN - Specifies the start of an OLE Object
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG Header;  /* Signature and length of this record */
   WORD Version;  /* Notes OLE implementation version */
   DWORD Flags;  /* See OLEREC_FLAG_xxx */
   WORD ClipFormat;       /* Clipboard format with which data should 
                              be rendered (see DDEFORMAT_xxx) */
   WORD AttachNameLength;  /* Attached file name length */
   WORD ClassNameLength;   /* Length of readable OLE class name */
   WORD TemplateNameLength; /* User during Insert New Object, 
                               but never saved to disk */
/* The Attachment Name (len=AttachNameLength) always follows... */
/* The Classname (optional) then follows... */
/* The Template Name (optional) then follows... */
} CDOLEBEGIN;
```

**Description :**

This structure specifies the start of an OLE Object.<br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note.<br>
<br>
  Header:			Defines this composite data item as a CDOLEBEGIN item.<br>
  Version:			Notes OLE implementation version. Set this to NOTES_OLEVERSION.<br>
  Flags:			Defines various attributes of the OLE object. See OLEREC_FLAG_xxx.<br>
  ClipFormat:		Clipboard format with which to render data.  See DDEFORMAT_xxx.<br>
  AttachNameLength:	Filename length (without the '\0' terminator) of the attached OLE object file.<br>
  ClassNameLength:	(Optional) Length of the object's readable OLE class name.<br>
  TemplateNameLength:	(Optional) Length of the object's template class name.<br>
<br>
The above fields are then followed by a series of zero or more packed strings, corresponding to the &quot;length&quot; parameters listed above.  These packed strings must appear in the same order as the &quot;length&quot; parameters.


**See Also :**
[CDOLEEND](/domino-c-api-docs/reference/Data/CDOLEEND)
---
