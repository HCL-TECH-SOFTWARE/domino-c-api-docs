##### Data Type : Composite Data
##### CDMACMETASEG - Segment of Macintosh Metafile Data
---
##### #include <editods.h>
**Description :**
A portion of a Macintosh metafile.  This record must be preceded by a 
CDMACMETAHEADER record.  Since metafiles can be large, but Domino and Notes 
have an internal limit of 65,536 bytes (64kB) for a segment, a metafile may be 
divided into segments of up to 64kB;  each segment must be preceded by a 
CDMACMETASEG record.

        Header           Tag identifying this as a CDMACMETASEG record
        DataSize        Actual size of metafile, in bytes
        SegSize         Size of segment

The segment size may actually be larger than the size of the metafile;  if the 
metafile is an odd number of bytes in length, a byte will be added to align 
data on a word boundary.
**See Also :**
[CDGRAPHIC](D:/md_files/CDGRAPHIC.md)
[CDMACMETAHEADER](D:/md_files/CDMACMETAHEADER.md)
---
