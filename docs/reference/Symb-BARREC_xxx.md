##### Symbolic Value : Composite Data
##### BARREC_xxx - CDBAR - Flags
---
##### #include <editods.h>
**Description :**
On-disk flags for CDBAR (Collapsible Sections). For collapsible sections 
indicated by a tab or a tab with a diagonal border, the CDBAR record (with its 
Flags member set to BARREC_BORDER_OTHER) is followed by a CDDATAFLAGS structure 
with its Flags member set to BARREC_DATA_BORDER_TAB (for tab) or 
BARREC_DATA_BORDER_DIAG (for diagonal).
**See Also :**
[CDBAR](D:/md_files/CDBAR.md)
[CDDATAFLAGS](D:/md_files/CDDATAFLAGS.md)
---
