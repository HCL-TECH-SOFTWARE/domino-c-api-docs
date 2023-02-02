##### Data Type : Composite Data
##### CDCGMMETA - Start of a CGM Metafile Record
---
##### #include <editods.h>
**Description :**
Identifies a CGM metafile embedded in a rich text field.  This record must be 
preceded by a CDGRAPHIC record.  A CDCGMMETA record may contain all or part of 
a CGM metafile, and is limited to 65,536 bytes (64K).

        Header                      Tag identifying this as a CDCGMMETA record
        mm                              CGM mapping mode - currently must be 
CGM_MAPMODE_ABSTRACT
        xExt                             Width of drawing in world coordinates
        yExt                             Height of drawing in world coordinates
        OriginalSize             Original display size of metafile, measured in 
"twips" (1/1440 inch)

This header is followed by up to 64K of metafile data.
**See Also :**
[CDGRAPHIC](D:/md_files/CDGRAPHIC.md)
[CGM_MAPMODE_xxx](D:/md_files/CGM_MAPMODE_xxx.md)
[RECTSIZE](D:/md_files/RECTSIZE.md)
---
