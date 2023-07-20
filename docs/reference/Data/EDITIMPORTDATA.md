##### Data Type : Import/Export
##### EDITIMPORTDATA - Used in editor imports.
---
```
#include <ixedit.h>
```

**Definition :**
```
typedef struct {
   char OutputFileName[OLDMAXPATH];  /* File to be filled by import
                                        with CD records */
   FONTID FontID;    /* font used at the current caret position */
} EDITIMPORTDATA;
```

**Description :**

This structure is passed to all editor imports.


**See Also :**
[EDITEXPORTDATA](/domino-c-api-docs/reference/Data/EDITEXPORTDATA)
[EDITIXDATA](/domino-c-api-docs/reference/Data/EDITIXDATA)
---
