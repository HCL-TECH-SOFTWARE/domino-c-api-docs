##### Function : Database
##### NSFDbGetBuildVersion - Get the Domino or Notes build number.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbGetBuildVersion(

	DBHANDLE  hDB,
	WORD far *retVersion);
```
**Description :**

This function returns the "major" portion of the build number of the Domino or 
Notes executable running on the system where the specified database resides. 
Use this information to determine what Domino or Notes release is running on a 
given system. The database handle input may represent a local database, or a 
database that resides on a Lotus Domino Server.

Domino or Notes Release 1.0 (all preliminary and final versions) are build 
numbers 1 to 81.

Domino or Notes Release 2.0 (all preliminary and final versions) are build 
numbers 82 to 93.

Domino or Notes Release 3.0 (all preliminary and final versions) are build 
numbers 94 to 118.

Domino or Notes Release 4.0 (all preliminary and final versions) are build 
numbers 119 to 136.

	Domino or Notes Release 4.1 (all preliminary and final versions) are 
build number 138.

	Domino or Notes Release 4.5 (all preliminary and final versions) are 
build number 140 - 145.

	Domino or Notes Release 4.6 (all preliminary and final versions) are 
build number 147.

	Domino or Notes Release 5.0 Beta 1 is build number 161. 

	Domino or Notes Release 5.0 Beta 2 is build number 163. 

	Domino or Notes Releases 5.0 - 5.0.11 are build number 166.

	Domino or Notes Release Rnext Beta 1 is build number 173.

	Domino or Notes Release Rnext Beta 2 is build number 176.

	Domino or Notes Release Rnext Beta 3 is build number 178.

	Domino or Notes Release Rnext Beta 4 is build number 179.

	Domino or Notes 6  Pre-release 1 is build number 183.

	Domino or Notes 6  Pre-release 2 is build number 185.

	Domino or Notes 6  Release Candidate is build number 190.

	Domino or Notes 6 - 6.0.2 are build number 190.

	Domino or Notes 6.0.3 - 6.5 are build numbers 191 to 194.

	Domino or Notes 7.0 Beta 2 is build number 254.

   Domino or Notes 9.0 is build number 400.
   Domino or Notes 9.0.1 is build number 405.

**Parameters :**
Input :
hDB  -  A handle to an open Domino database.  If the database is LOCAL, then the build number returned will be for the LOCAL  version of Domino or Notes and if the database is REMOTE, then the build number returned will be for the REMOTE version of the Lotus Domino Server.

Output :
(routine)  -  Return status from this call, which is NOERROR in all cases.


retVersion  -  The address of a WORD in which the major portion of the build number is returned.


**Sample Usage :**
```

   /* Get Major Domino or Notes Build Number.  If database is remote, then   */
   /* you get the Build running on the Server. If database is local*/
   /* then you get the current machine's Build.                    */
 
  if (error_status = NSFDbGetBuildVersion(db_handle,
                                           &major_build_num))
       goto Exit;

```
**See Also :**
[NSFDbOpen](/domino-c-api-docs/reference/Func/NSFDbOpen)
[NSFDbOpenExtended](/domino-c-api-docs/reference/Func/NSFDbOpenExtended)
[NSFDbPathGet](/domino-c-api-docs/reference/Func/NSFDbPathGet)
[OSPathNetParse](/domino-c-api-docs/reference/Func/OSPathNetParse)
---
