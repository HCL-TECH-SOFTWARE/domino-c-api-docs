##### Data Type : Composite Data
##### CDWINMETAHEADER - Start of a Windows GDI Metafile Record
---
##### #include <editods.h>
**Description :**
Identifies a Windows Graphics Device Interface (GDI) metafile embedded in a 
rich text field.  This record must be preceded by a CDGRAPHIC record.  Since 
Windows GDI metafiles can be large, but Domino and Notes have an internal limit 
of 65,536 bytes (64kB) for a segment, a metafile may be divided into segments 
of up to 64kB;  each segment must be preceded by a CDWINMETASEG record.

  Header            Tag identifying this as a CDWINMETAHEADER record
  mm                Windows mapping mode
  xExt              Width of drawing in world coordinates
  yExt              Height of drawing in world coordinates
  OriginalDisplaySize Original Display size of metafile,
                    measured in "twips" (1/1440 inch)
  MetafileSize      Total size of metafile data in bytes
  SegCount          Number of CDWINMETASEG records

This header is followed by the segments of metafile data.
**See Also :**
[CDGRAPHIC](D:/md_files/CDGRAPHIC.md)
[CDWINMETASEG](D:/md_files/CDWINMETASEG.md)
---
