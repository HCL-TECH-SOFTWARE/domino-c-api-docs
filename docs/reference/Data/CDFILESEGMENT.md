##### Data Type : Rich Text
##### CDFILESEGMENT - Structure which defines a CSS segment.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
 LSIG Header;  /* Signature and Length */
 WORD  DataSize;  /* Actual Size of image bits in bytes, ignoring any filler */
 WORD  SegSize;   /*  Size of segment, is equal to or larger than DataSize 
         if filler byte added to maintain word boundary */  
 DWORD Flags;  /* currently unused, but someday someone will be happy this is 
here */
 DWORD Reserved;  /* Reserved for future use */
 /* File bits for this segment */
} CDFILESEGMENT;


**Description :**

This structure defines the file segment data of a Cascading Style Sheet (CSS) and follows a CDFILEHEADER structure.  The number of segments in the file is specified in the CDFILEHEADER record.<br>

<ul>The fields in this structure are:<br>
<br>
Header - Defines this composite data item as a CDFILESEGMENT item.<br>
<br>
DataSize - Size of CSS in bytes<br>
<br>
SegSize - Size of segment. This is equal to or larger than DataSize if a filler byte is added to maintain the word boundary.<br>
<br>
Flags - Flags (currently unused)<br>
 <br>
Reserved - Reserved for future use<br>
<br>
File bits for this segment (the CSS and the optional filler byte) follow this record.<br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note. </ul>



**See Also :**
[CDFILEHEADER](/domino-c-api-docs/reference/Data/CDFILEHEADER)
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
---
