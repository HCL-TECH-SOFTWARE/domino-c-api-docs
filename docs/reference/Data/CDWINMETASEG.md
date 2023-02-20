##### Data Type : Composite Data
##### CDWINMETASEG - Segment of Windows GDI Metafile Data
---
```
#include <editods.h>
```
**Description :**

A portion of a Windows GDI metafile.  This record must be preceded by a 
CDWINMETAHEADER record.  Since Windows GDI metafiles can be large, but Domino 
and Notes have an internal limit of 65,536 bytes (64kB) for a segment, a 
metafile may be divided into segments of up to 64kB;  each segment must be 
preceded by a CDWINMETASEG record.

        Header           Tag identifying this as a CDWINMETASEG record
        DataSize        Actual size of metafile, in bytes
        SegSize         Size of segment

The segment size may actually be larger than the size of the metafile;  if the 
metafile is an odd number of bytes in length, a byte will be added to align 
data on a word boundary.

**See Also :**
[CDGRAPHIC](/reference/Data/CDGRAPHIC)
[CDWINMETAHEADER](/reference/Data/CDWINMETAHEADER)
---
