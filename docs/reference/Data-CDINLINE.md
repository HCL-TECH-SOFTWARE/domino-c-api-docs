##### Data Type : Composite Data
##### CDINLINE - Pertains to shared resources and/or shared code in a form.
---
##### #include <editods.h>
**Description :**
This CD Record gives information pertaining to shared resources and/or shared 
code in a form.  A CDINLINE record may be preceded by a CDBEGINRECORD and 
followed by a CDRESOURCE and then a CDENDRECORD.  The fields in this record are:

Header - Signature and Length of this CD record.
wDatalength - Reserved for future use. Must be zero. 
dwFlags - see INLINE_FLAG_xxx
dwReserved[4] - Reserved for future use.

**See Also :**
[CDBEGINRECORD](D:/md_files/CDBEGINRECORD.md)
[CDENDRECORD](D:/md_files/CDENDRECORD.md)
[CDRESOURCE](D:/md_files/CDRESOURCE.md)
[INLINE_FLAG_xxx](D:/md_files/INLINE_FLAG_xxx.md)
[INLINE_VERSION1](D:/md_files/INLINE_VERSION1.md)
---
