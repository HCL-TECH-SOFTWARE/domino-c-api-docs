##### Symbolic Value : Import/Export
##### EXPKG_xxx - Offsets within PKG_EXPORT for exports.
---
##### #include <globerr.h>
**Description :**
On the Mac, since all ixports are compiled into Notes, their strings must have 
unique IDs, we avoid using a separate PKG for each by defining the offset of 
each ixport's first string.  Under Windows and PM, since each ixport is a 
separate DLL with separate DS space, all offsets are set to 0.

NOTE:  TARGA, and WMF are not to be ported to the Mac, therefore no offsets are 
provided for them.
**See Also :**
[IMPKG_xxx](D:/md_files/IMPKG_xxx.md)
---
