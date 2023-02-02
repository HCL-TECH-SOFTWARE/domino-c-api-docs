##### Function : Rich Text
##### MapV3ColorToExtColor - Convert a Notes Release 3 color index to a Notes Release 4 compatible color index.
---
##### #include <colorid.h>
WORD LNPUBLIC **MapV3ColorToExtColor(**

	WORD  color);
**Description :**
In Notes Release 4, the number of choices for a view's background color and for 
a form's paper color have increased and the color indexes have changed between 
Notes Release 3 and Notes Release 4.  This function maps a Notes Release 3 
color index to the Notes Release 4 color index.  These color indexes are used 
in the structures, CDDOCUMENT and VIEW_TABLE_FORMAT2.
**Parameters :**
Input :
color  -  Notes Release 4 color index.

Output :
(routine)  -  Notes Release 4 color  index that maps to the given Release 3 form or view background color.


**See Also :**
[CDDOCUMENT](D:/md_files/CDDOCUMENT.md)
[VIEW_TABLE_FORMAT2](D:/md_files/VIEW_TABLE_FORMAT2.md)
[NOTES_COLOR_xxx](D:/md_files/NOTES_COLOR_xxx.md)
[MapExtColorToV3Color](D:/md_files/MapExtColorToV3Color.md)
---
