##### Data Type : Navigators
##### VIEWMAP_DATASET_RECORD - Navigator settings CD record.
---
##### #include <vmods.h>
**Description :**
The VIEWMAP_DATASET_RECORD stores the settings and defaults for a Navigator.  
The fields in this structure are:

Header            Defines this composite data item as a
                  VIEWMAP_DATASET_RECORD item.
Version           Version number of this structure.
ViewNameLen       Length of the inital view name;  may be 0.
Gridsize          Size of any displayed grid, in pixels.
Flags             Option flags (see VM_DSET_xxx).
bAutoAdjust       If TRUE, automatically adjust the display to
                  show as much of the Navigator as possible.
BGColor           Background color for the Navigator.
SeqNums           Each type of graphical object is numbered in
                  sequence.  This array stores the highest number
                  assigned in this navigator.
StyleDefaults     Structure containing the default settings for
                  graphical elements.
NumPaletteEntries Number of color palette entries required to
                  display this Navigator.
ViewDesignType    Design type of the initial view.
BGColorValue
spare             Reserved; must be 0.

**See Also :**
[VM_MAX_OBJTYPES](D:/md_files/VM_MAX_OBJTYPES.md)
[VIEWMAP_STYLE_DEFAULTS](D:/md_files/VIEWMAP_STYLE_DEFAULTS.md)
[VIEWMAP_VERSION](D:/md_files/VIEWMAP_VERSION.md)
[VM_DSET_xxx](D:/md_files/VM_DSET_xxx.md)
---
