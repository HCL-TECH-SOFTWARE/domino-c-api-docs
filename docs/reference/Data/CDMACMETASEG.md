##### Data Type : Composite Data
##### CDMACMETASEG - Segment of Macintosh Metafile Data
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   LSIG Header; /* Signature and Length */
   WORD  DataSize; /* Actual Size of metafile, in bytes
     (ignoring any filler) */
   WORD  SegSize;  /* Size of segment, in bytes */
 /* Metafile Bits for this segment. Each segment
  must be <= 64K bytes. */
} CDMACMETASEG;

**Description :**

A portion of a Macintosh metafile.  This record must be preceded by a CDMACMETAHEADER record.  Since metafiles can be large, but Domino and Notes have an internal limit of 65,536 bytes (64kB) for a segment, a metafile may be divided into segments of up to 64kB;  each segment must be preceded by a CDMACMETASEG record.<br>
<br>
        Header           Tag identifying this as a CDMACMETASEG record<br>
        DataSize        Actual size of metafile, in bytes<br>
        SegSize         Size of segment<br>
<br>
The segment size may actually be larger than the size of the metafile;  if the metafile is an odd number of bytes in length, a byte will be added to align data on a word boundary.


**See Also :**
[CDGRAPHIC](/domino-c-api-docs/reference/Data/CDGRAPHIC)
[CDMACMETAHEADER](/domino-c-api-docs/reference/Data/CDMACMETAHEADER)
---
