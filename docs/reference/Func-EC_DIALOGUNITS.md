##### Function : Rich Text
##### EC_DIALOGUNITS - Evaluates the Flags member of CDEMBEDDEDCTL against EC_FLAG_UNITS
---
##### #include <editods.h>
BOOL **EC_DIALOGUNITS(**

	WORD  flags);
**Description :**
Implemented as a macro:

#define EC_DIALOGUNITS(flags)   ((flags & EC_FLAG_UNITS) == 
EC_FLAG_DIALOGUNITS)
**Parameters :**
Input :
flags  -  EC_FLAG_xxx

Output :
(routine)  -  Returns TRUE if width/height of specified flag have been adjusted to fit contents, FALSE otherwise.


**See Also :**
[CDEMBEDDEDCTL](D:/md_files/CDEMBEDDEDCTL.md)
[EC_FLAG_xxx](D:/md_files/EC_FLAG_xxx.md)
---
