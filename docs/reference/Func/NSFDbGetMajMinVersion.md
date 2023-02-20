##### Function : Database
##### NSFDbGetMajMinVersion - Get information about code level running on a machine
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbGetMajMinVersion(

	DBHANDLE  hDb,
	BUILDVERSION far *retBuildVersion);
```
**Description :**

This function returns a BUILDVERSION structure which contains all types of 
information about the level of code running on a machine.  See BUILDVERSION 
structure for more information.

**Parameters :**
Input :
hDb  -  A handle to an open Notes database.  If the database is LOCAL, then the build information returned will be for the LOCAL version of Notes and if the database is REMOTE, then the build version returned will be for the REMOTE version of the Notes Server.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully obtained Major/Minor Version.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


retBuildVersion  -  The address of a BUILDVERSION structure where information will be returned.  This structure will be all 0's if the database is remote and the remote server does not support this function.


**Sample Usage :**
```
BUILDVERSION bv;

.
.
.

 error = NSFDbOpen(argv[1], &db_handle);
 if (!error)
  {
  error = NSFDbGetMajMinVersion(db_handle, &bv);
  NSFDbClose(db_handle);
  if (!error)
   {
   printf("%d\t%d\t%d\t%d\t%d\t%d\n", bv.MajorVersion, bv.MinorVersion, 
bv.QMRNumber, bv.QMUNumber, bv.HotfixNumber, bv.Flags);
   }
  else
   {
   xprintf("Error getting version!\n");
   }
  }
```
**See Also :**
[BLDVERFLAGS_xxx](/reference/Symb/BLDVERFLAGS_xxx)
[BUILDVERSION](/reference/Data/BUILDVERSION)
[NSFDbOpen](/reference/Func/NSFDbOpen)
---
