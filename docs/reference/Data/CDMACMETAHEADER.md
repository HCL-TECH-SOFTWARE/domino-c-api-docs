##### Data Type : Composite Data
##### CDMACMETAHEADER - Start of a Macintosh Metafile Record
---
```
#include <editods.h>
```
**Description :**

Identifies a Macintosh metafile embedded in a rich text field.  This record 
must be preceded by a CDGRAPHIC record.  Since metafiles can be large, but 
Domino and Notes has an internal limit of 65,536 bytes (64kB) for a segment, a 
metafile may be divided into segments of up to 64kB;  each segment must be 
preceded by a CDMACMETASEG record.

        Header                          Tag identifying this as a 
CDMACMETAHEADER record
        OriginalDisplaySize  Original display size of metafile, measured in 
"twips" (1/1440 inch)
        MetafileSize                 Total size of metafile data in bytes
        SegCount                     Number of CDMACMETASEG records

This header is followed by the segments of metafile data.

**See Also :**
[CDGRAPHIC](/reference/Data/CDGRAPHIC)
[CDMACMETASEG](/reference/Data/CDMACMETASEG)
---
