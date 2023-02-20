##### Function : Database
##### NSFDbSetOptions - Set option flags for a database.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbSetOptions(

	DBHANDLE  hDB,
	DWORD  DbOptions,
	DWORD  Mask);
```
**Description :**

Set the option flags for the database.  The option flags are described in the 
entry DBOPTION_xxx.

**Parameters :**
Input :
hDB  -  Handle of the database.

DbOptions  -  New option flag settings.

Mask  -  Bit mask that controls which options are updated.  Only the specified option bits will be updated with the DbOptions value.

Output :
(routine)  -  Return status from this call -- indicates either success, or what the error is.  The return codes include:

NOERROR



**Sample Usage :**
```
...
/* enable Full Text indexing */
status = NSFDbSetOptions(db_handle, DBOPTION_FT_INDEX, DBOPTION_FT_INDEX);
...
/* disable Full Text indexing */
status = NSFDbSetOptions(db_handle, (DWORD)0, DBOPTION_FT_INDEX);
...
/* enable Full Text indexing, disable uniform replica access */
status = NSFDbSetOptions(db_handle, DBOPTION_FT_INDEX, 
                         DBOPTION_FT_INDEX | DBOPTION_UNIFORM_ACCESS);
...
```
**See Also :**
[NSFDbGetOptions](/reference/Func/NSFDbGetOptions)
[DBOPTION_xxx](/reference/Symb/DBOPTION_xxx)
---
