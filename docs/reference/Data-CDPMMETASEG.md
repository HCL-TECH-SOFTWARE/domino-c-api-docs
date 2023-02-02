##### Data Type : Composite Data
##### CDPMMETASEG - Segment of Presentation Manager GPI Metafile Data
---
##### #include <editods.h>
**Description :**
A portion of a Presentation Manager GPI metafile.  This record must be preceded 
by a CDPMMETAHEADER record.  Since metafiles can be large, but Domino and Notes 
have an internal limit of 65,536 bytes (64kB) for a segment, a metafile may be 
divided into segments of up to 64kB;  each segment must be preceded by a 
CDPMMETASEG record.

        Header           Tag identifying this as a CDPMMETASEG record
        DataSize        Actual size of metafile, in bytes
        SegSize         Size of segment

The segment size may actually be larger than the size of the metafile;  if the 
metafile is an odd number of bytes in length, a byte will be added to align 
data on a word boundary.
**See Also :**
[CDGRAPHIC](D:/md_files/CDGRAPHIC.md)
[CDPMMETAHEADER](D:/md_files/CDPMMETAHEADER.md)
---
