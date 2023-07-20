##### Data Type : File Attachment
##### ASSOCIATEDFILESDATA - OLE Object - List of associated files.
---
```
#include <oleods.h>
```

**Definition :**
```
typedef struct {        
   WORD wLength;           /* Size of this structure including both
                              fixed and variable sections */
   WORD wcAssociatedFILEs; /* Number of Associated $FILEs */
   WORD wReserved1;        /* Unused, must be 0 */
   WORD wReserved2;        /* Unused, must be 0 */
   WORD wReserved3;        /* Unused, must be 0 */
/*
   The variable length portions go here in the following order:
   Associated $FILEs - array or list of Associated FILES
   (OLEOBJASSOCIATEDFILE structures)
*/
} ASSOCIATEDFILESDATA;
```

**Description :**

List of attached files associated with an embedded OLE 2 object.


**See Also :**
[ASSOCIATEDFILE](/domino-c-api-docs/reference/Data/ASSOCIATEDFILE)
---
