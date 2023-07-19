##### Data Type : Composite Data
##### CDPMMETASEG - Segment of Presentation Manager GPI Metafile Data
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
 /* PM Metafile Bits for this segment. Each segment
  must be <= 64K bytes. */
} CDPMMETASEG;

**Description :**

A portion of a Presentation Manager GPI metafile.  This record must be preceded by a CDPMMETAHEADER record.  Since metafiles can be large, but Domino and Notes have an internal limit of 65,536 bytes (64kB) for a segment, a metafile may be divided into segments of up to 64kB;  each segment must be preceded by a CDPMMETASEG record.<br>
<br>
        Header           Tag identifying this as a CDPMMETASEG record<br>
        DataSize        Actual size of metafile, in bytes<br>
        SegSize         Size of segment<br>
<br>
The segment size may actually be larger than the size of the metafile;  if the metafile is an odd number of bytes in length, a byte will be added to align data on a word boundary.


**See Also :**
[CDGRAPHIC](/domino-c-api-docs/reference/Data/CDGRAPHIC)
[CDPMMETAHEADER](/domino-c-api-docs/reference/Data/CDPMMETAHEADER)
---
