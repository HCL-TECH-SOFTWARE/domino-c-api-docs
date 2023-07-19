##### Data Type : Composite Data
##### CDCGMMETA - Start of a CGM Metafile Record
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   LSIG     Header;       /* Signature and Length */
   SWORD    mm;           /* CGM mapping mode (see CGM_MAPMODE_xxx) */
   SWORD    xExt,yExt;    /* Extents, in world coordinates */
   RECTSIZE OriginalSize; /* Original display size, in twips */
   /* CGM Metafile bits follow (must be <= 64K bytes total) */
} CDCGMMETA;

**Description :**

Identifies a CGM metafile embedded in a rich text field.  This record must be preceded by a CDGRAPHIC record.  A CDCGMMETA record may contain all or part of a CGM metafile, and is limited to 65,536 bytes (64K).<br>
<br>
        Header                      Tag identifying this as a CDCGMMETA record<br>
        mm                              CGM mapping mode - currently must be CGM_MAPMODE_ABSTRACT<br>
        xExt                             Width of drawing in world coordinates<br>
        yExt                             Height of drawing in world coordinates<br>
        OriginalSize             Original display size of metafile, measured in &quot;twips&quot; (1/1440 inch)<br>
<br>
This header is followed by up to 64K of metafile data.


**See Also :**
[CDGRAPHIC](/domino-c-api-docs/reference/Data/CDGRAPHIC)
[CGM_MAPMODE_xxx](/domino-c-api-docs/reference/Symb/CGM_MAPMODE_xxx)
[RECTSIZE](/domino-c-api-docs/reference/Data/RECTSIZE)
---
