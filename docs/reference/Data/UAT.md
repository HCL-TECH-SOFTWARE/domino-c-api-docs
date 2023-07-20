##### Data Type : HTML
##### UAT - URL Addressable Type
---
```
#include <urltypes.h>
```

**Definition :**
```
typedef enum _UAT
{
    UAT_None                    = 0,
    UAT_Server                  = 1,
    UAT_Database                = 2,
    UAT_View                    = 3,
    UAT_Form                    = 4,
    UAT_Navigator               = 5,
    UAT_Agent                   = 6,
    UAT_Document                = 7,
    UAT_Filename                = 8,    /* internal filename of attachment */
    UAT_ActualFilename          = 9,    /* external filename of attachment if 
different */
    UAT_Field                   = 10,
    UAT_FieldOffset             = 11,
    UAT_FieldSuboffset          = 12,
    UAT_Page                    = 13,
    UAT_FrameSet                = 14,
    UAT_ImageResource           = 15,
    UAT_CssResource             = 16,
    UAT_JavascriptLib           = 17,
    UAT_FileResource            = 18,
    UAT_About                   = 19,
    UAT_Help                    = 20,
    UAT_Icon                    = 21,
    UAT_SearchForm              = 22,
    UAT_SearchSiteForm          = 23,
    UAT_Outline                 = 24,

    UAT_NumberOfTypes           /* must be the last one */
} UAT;
```

**Description :**

This can be used to determine the URL address type, some operation on the generated HTML text should be done according to the URL type. For more information, please refer the samples released with the C API toolkit


**Sample Usage :**
```
see sample html/convattach
```

**See Also :**
[HTMLAPI_URLTargetComponent](/domino-c-api-docs/reference/Data/HTMLAPI_URLTargetComponent)
---
