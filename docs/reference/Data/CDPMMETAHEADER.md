##### Data Type : Composite Data
##### CDPMMETAHEADER - Start of a Presentation Manager GPI Metafile Record
---
```
#include <editods.h>
```
**Description :**

Identifies a Presentation Manger GPI metafile embedded in a rich text field.  
This record must be preceded by a CDGRAPHIC record.  Since metafiles can be 
large, but Domino and Notes have an internal limit of 65,536 bytes (64kB) for a 
segment, a metafile may be divided into segments of up to 64kB;  each segment 
must be preceded by a CDPMMETASEG record.

  Header             Tag identifying this as a CDPMMETAHEADER record
  mm                 PM mapping mode
  xExt               Width of drawing in world coordinates
  yExt               Height of drawing in world coordinates
  OriginalDisplaySize  Original display size of metafile,
                     measured in "twips" (1/1440 inch)
  MetafileSize       Total size of metafile data in bytes
  SegCount           Number of CDPMMETASEG records

This header is followed by the segments of metafile data.

**See Also :**
[CDGRAPHIC](/reference/Data/CDGRAPHIC)
[CDPMMETASEG](/reference/Data/CDPMMETASEG)
---
