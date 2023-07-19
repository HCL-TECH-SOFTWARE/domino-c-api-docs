##### Data Type : Rich Text
##### HEAD_DESC - Header/Footer Data Structure Passed to Import/Export Modules
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   BYTE FontPitchAndFamily; /* Font pitch and family */
   char FontName[MAXFACESIZE]; /* Font name */
   FONTID Font;    /* Font ID */
   WORD HeadLength;  /* string length not including '\0' */
 /* Header string follows */
} HEAD_DESC;

**Description :**

This data structure is passed to Import/Export modules to describe the header or footer for a document.<br>
<br>
        FontPitchAndFamily        Pitch and font family of font used to display the data<br>
        FontName                           Name of font to use<br>
        Font                                       ID of font to use<br>
        HeadLength                       Total string length of header or footer<br>



**See Also :**
[EDITEXPORTDATA](/domino-c-api-docs/reference/Data/EDITEXPORTDATA)
[HEAD_DESC_BUFFER](/domino-c-api-docs/reference/Data/HEAD_DESC_BUFFER)
---
