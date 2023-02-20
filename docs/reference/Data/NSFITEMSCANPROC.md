##### Data Type : Item (Field)
##### NSFITEMSCANPROC - Action routine for each item found by NSFItemScan.
---
```
#include <nsfnote.h>
```
**Description :**

This typedef defines the interface to the routine called by NSFItemScan().  
Under Windows, the routine must be exported in the application's .DEF file.

The address of a routine with this interface is passed as a parameter to 
NSFItemScan().  The routine will be called once for each item found in a note.  
The first parameter is supplied in the call to NSFItemScan() and is used in the 
case where the caller of NSFItemScan() needs to pass data to this routine.  If 
this routine returns an error, NSFItemScan will halt and return that error.

**See Also :**
[NSFItemScan](/reference/Func/NSFItemScan)
---
