##### Function : Font
##### BYTEMASK - Create a mask byte in a DWORD, to be used to reference the bytes in a FONTID.
---
##### #include <fontid.h>
DWORD **BYTEMASK(**

	DWORD  leftshift);
**Description :**
Returns a DWORD containing a byte mask in one of its bytes. The byte mask may 
then be used to reference the bytes in a FONTID.  

Implemented as a macro:

#define BYTEMASK(leftshift) ((DWORD)((DWORD)0x000000ff << (leftshift)))
**Parameters :**
Input :
leftshift  -  The number of bits the number 0x000000ff must be left-shifted to create the desired byte mask.  Use one of the values defined in FONT_xxx_SHIFT to generate a mask for one of the bytes in a FONTID.

Output :
(routine)  -  A DWORD in which one of the bytes has all its bits set, and all the bits in the other bytes are cleared.


**Sample Usage :**
```
#define FontSetColor(fontid,colorid) (((DWORD)(fontid) & 
~BYTEMASK(FONT_COLOR_SHIFT)) | ((DWORD)(colorid)<<FONT_COLOR_SHIFT))
```
**See Also :**
[FontSetColor](D:/md_files/FontSetColor.md)
[FontSetFaceID](D:/md_files/FontSetFaceID.md)
[FontSetSize](D:/md_files/FontSetSize.md)
[FontSetStyle](D:/md_files/FontSetStyle.md)
[FONT_xxx_SHIFT](D:/md_files/FONT_xxx_SHIFT.md)
---
