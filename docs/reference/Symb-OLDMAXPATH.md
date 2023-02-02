##### Symbolic Value : Limits
##### OLDMAXPATH - Maximum pathname (backward-compatible version).
---
##### #include <names.h>
**Description :**
Before Release 4 of the Notes C API, MAXPATH was 256 for the Macintosh, 
Netware, and Unix platforms.  For all other platforms, it was 100.  Release 4 
included support for Windows 32-bit long filenames, requiring MAXPATH to be 
increased to 256.  For backwards compatibility, OLDMAXPATH is defined and has 
the same definition of MAXPATH in Release 3 and earlier.  The MAXPATH 
definition in Release 4 and later release is 256 for all platforms.
**See Also :**
[MAXPATH](D:/md_files/MAXPATH.md)
---
