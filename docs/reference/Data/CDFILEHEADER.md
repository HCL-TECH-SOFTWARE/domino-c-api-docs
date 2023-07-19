##### Data Type : Rich Text
##### CDFILEHEADER - Structure which defines a CSS header.
---
```
#include <editods.h>
```

**Definition :**

typedef struct{
 LSIG Header;  /* Signature and Length */
 WORD  FileExtLen;  /* Length of file extenstion */
 DWORD FileDataSize; /* Size (in bytes) of the file data */
 DWORD SegCount;  /* Number of CDFILESEGMENT records expected to follow */
 DWORD Flags;  /* Flags (currently unused) */
 DWORD Reserved;  /* Reserved for future use */
 /* Variable length string follows (not null terminated).
  This string is the file extension for the file. */
} CDFILEHEADER;

**Description :**

This structure is used to define a Cascading Style Sheet (CSS) that is part of a Domino database.  CDFILESEGMENT structure(s) follow the CDFILEHEADER.
<ul><br>
<br>
The fields in this structure are:<br>
<br>
Header - Defines this composite data item as a CDFILEHEADER item.<br>
<br>
FileExtLen - Length of file extension<br>
<br>
FileDataSize - Size (in bytes) of the file data<br>
<br>
SegCount - Number of CDFILESEGMENT records expected to follow<br>
<br>
Flags - Flags (currently unused)<br>
 <br>
Reserved - Reserved for future use<br>
<br>
A non-null terminated variable length string follows. This string is the file extension for the file. For example: &quot;css&quot;.<br>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE.  Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note. </ul>



**See Also :**
[CDFILESEGMENT](/domino-c-api-docs/reference/Data/CDFILESEGMENT)
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
---
