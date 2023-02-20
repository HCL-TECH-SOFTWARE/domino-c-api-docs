##### Function : Database
##### NSFDbCompactExtendedExt2 - Compresses a local Domino database.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbCompactExtendedExt2(

	const char *Pathname,
	DWORD  Options,
	DWORD  Options2,
	NUMBER *OriginalSize,
	NUMBER *CompactedSize);
```
**Description :**

This function compresses a local database  to remove the space left by deleting 
documents, freeing up disk space.  Deletion stubs however, are left intact in 
the database.  This function is the same as NSFDbCompactExtended, but it allows 
more options.

**Parameters :**
Input :
Pathname  -  A pointer to the pathname of a Domino database.  The string must be null-terminated.  The directory part of the path may be omitted if the database is in the data directory.  The filename extension may be omitted if it is ".NSF".

Options  -  See DBCOMPACT_xxx.  If no options are desired, this parameter may be set to 0 (Zero).

Options2  -  See DBCOMPACT2_xxx,the parameter to allow customers to turn on/off design compression, data compression and DAOS for a given database.
#define DBCOMPACT2_COMPRESS_DESIGN_NS	0x00000400	/* TRUE if design note non-summary should be compressed */
#define DBCOMPACT2_UNCOMPRESS_DESIGN_NS	0x00000800	/* TRUE if design note non-summary should be uncompressed */

#define DBCOMPACT2_COMPRESS_DATA_DOCS	0x00004000	/* TRUE if all data note non-summary should be compressed */
#define DBCOMPACT2_UNCOMPRESS_DATA_DOCS	0x00008000	/* TRUE if all data note non-summary should be uncompressed */

#define DBCOMPACT2_FORCE_DAOS_ON		0x00020000	/* enable compact TO DAOS */
#define DBCOMPACT2_FORCE_DAOS_OFF		0x00040000	/* enable compact FROM DAOS */


Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is.


OriginalSize  -  Returns the OriginalSize of the database in a NUMBER *.

CompactedSize  -  Returns the CompactedSize of the database in a NUMBER *.


**See Also :**
[NSFDbCompact](/reference/Func/NSFDbCompact)
[NSFDbCompactExtended](/reference/Func/NSFDbCompactExtended)
---
