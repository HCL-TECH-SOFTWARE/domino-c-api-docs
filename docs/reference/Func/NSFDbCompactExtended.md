##### Function : Database
##### NSFDbCompactExtended - Compresses a local Domino database with extended options.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbCompactExtended(

	const char *Pathname,
	DWORD  Options,
	DWORD *retStats);
```
**Description :**

This function compresses a local database  to remove the space left by deleting 
documents, freeing up disk space.  Deletion stubs however, are left intact in 
the database.  This function is the same as NSFDbCompact, but it allows more 
options.

**Parameters :**
Input :
Pathname  -  A pointer to the pathname of a Domino database.  The string must be null-terminated.  The directory part of the path may be omitted if the database is in the data directory.  The filename extension may be omitted if it is ".NSF".

Options  -  See DBCOMPACT_xxx.  If no options are desired, this parameter may be set to 0 (Zero).

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR

ERR_NOT_NSF

ERR_NSF_VERSION

ERR_NOT_LOCAL - An attempt was made to compact a non-local Domino database.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user. 


retStats  -  A pointer to an array of two DWORDs in which database statistics are returned.  The first DWORD contains the size in bytes of the Domino database before being compacted, while the second DWORD contains the size of the database after being compacted.


**Sample Usage :**
```
char         *db_filename;  /* pathname of source database */
STATUS       error;         /* return status from API calls */
DWORD         Options = 0;   /* compact options */
DWORD        Stats[2];      /* status return code */

/* set db_filename to the name of the database to be compacted */

if (error = NSFDbCompactExtended (db_filename, Options, &Stats[0]))
{
   printf ("error = %x\n", ERR(error));
   return (ERR(error));
}
printf ("\nCompaction of %s completed\n", db_filename);
printf ("Size of %s before compaction:  %lu\n", db_filename, Stats[0]);
printf ("Size of %s after compaction:   %lu\n", db_filename, Stats[1]);

```
**See Also :**
[DBCOMPACT_xxx](/reference/Symb/DBCOMPACT_xxx)
[NSFDbCompact](/reference/Func/NSFDbCompact)
---
