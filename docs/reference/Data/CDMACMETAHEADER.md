##### Data Type : Composite Data
##### CDMACMETAHEADER - Start of a Macintosh Metafile Record
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   LSIG Header;  /* Signature and Length */
   RECTSIZE OriginalDisplaySize; /* Original disp. size, in twips */
   DWORD MetafileSize; /* Total size of metafile, in bytes */
   WORD  SegCount;  /* Number of CDMACMETASEG records */
 /* Metafile segments Follow */
} CDMACMETAHEADER;
```

**Description :**

Identifies a Macintosh metafile embedded in a rich text field.  This record must be preceded by a CDGRAPHIC record.  Since metafiles can be large, but Domino and Notes has an internal limit of 65,536 bytes (64kB) for a segment, a metafile may be divided into segments of up to 64kB;  each segment must be preceded by a CDMACMETASEG record.<br>
<br>
        Header                          Tag identifying this as a CDMACMETAHEADER record<br>
        OriginalDisplaySize  Original display size of metafile, measured in &quot;twips&quot; (1/1440 inch)<br>
        MetafileSize                 Total size of metafile data in bytes<br>
        SegCount                     Number of CDMACMETASEG records<br>
<br>
This header is followed by the segments of metafile data.


**See Also :**
[CDGRAPHIC](/domino-c-api-docs/reference/Data/CDGRAPHIC)
[CDMACMETASEG](/domino-c-api-docs/reference/Data/CDMACMETASEG)
---
