##### Data Type : Rich Text
##### HEAD_DESC - Header/Footer Data Structure Passed to Import/Export Modules
---
```
#include <editods.h>
```
**Description :**

This data structure is passed to Import/Export modules to describe the header 
or footer for a document.

        FontPitchAndFamily        Pitch and font family of font used to display 
the data
        FontName                           Name of font to use
        Font                                       ID of font to use
        HeadLength                       Total string length of header or footer


**See Also :**
[EDITEXPORTDATA](/domino-c-api-docs/reference/Data/EDITEXPORTDATA)
[HEAD_DESC_BUFFER](/domino-c-api-docs/reference/Data/HEAD_DESC_BUFFER)
---
