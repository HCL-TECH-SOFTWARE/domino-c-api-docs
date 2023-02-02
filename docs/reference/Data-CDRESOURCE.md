##### Data Type : Composite Data
##### CDRESOURCE - A CD structure which defines a Domino Resource.
---
##### #include <rsrcods.h>
**Description :**
This CD record defines a resource within a database.  There may be many 
resources defined within a particular database.  A resource can be an image, an 
applet, a shared field or a script library.

WSIG Header   Signature and length
DWORD Flags   CDRESOURCE_FLAGS_xxx
WORD Type   CDRESOURCE_TYPE_xxx
WORD  ResourceClass  CDRESOURCE_CLASS_xxx
WORD Length1   depends on type 
WORD ServerHintLength length of the server hint
WORD FileHintLength  length of the file hint 
BYTE Reserved

**See Also :**
[CDRESOURCE_CLASS_xxx](D:/md_files/CDRESOURCE_CLASS_xxx.md)
[CDRESOURCE_FLAGS_xxx](D:/md_files/CDRESOURCE_FLAGS_xxx.md)
[CDRESOURCE_TYPE_xxx](D:/md_files/CDRESOURCE_TYPE_xxx.md)
---
