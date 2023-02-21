##### Data Type : Composite Data
##### CDOLEBEGIN - Specifies the start of an OLE Object
---
```
#include <editods.h>
```
**Description :**

This structure specifies the start of an OLE Object.

Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API 
programs that run on non-Intel architecture platforms must perform 
host/canonical conversion on CD record structures such as this when accessing 
rich text item data in a note.

  Header:   Defines this composite data item as a CDOLEBEGIN item.
  Version:   Notes OLE implementation version. Set this to NOTES_OLEVERSION.
  Flags:   Defines various attributes of the OLE object. See OLEREC_FLAG_xxx.
  ClipFormat:  Clipboard format with which to render data.  See DDEFORMAT_xxx.
  AttachNameLength: Filename length (without the '\0' terminator) of the 
attached OLE object file.
  ClassNameLength: (Optional) Length of the object's readable OLE class name.
  TemplateNameLength: (Optional) Length of the object's template class name.

The above fields are then followed by a series of zero or more packed strings, 
corresponding to the "length" parameters listed above.  These packed strings 
must appear in the same order as the "length" parameters.

**See Also :**
[CDOLEEND](/domino-c-api-docs/reference/Data/CDOLEEND)
---
