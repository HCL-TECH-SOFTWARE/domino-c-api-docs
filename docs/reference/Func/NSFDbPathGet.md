##### Function : Database
##### NSFDbPathGet - Given a database handle, get the file name string.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbPathGet(

	DBHANDLE  hDB,
	char far *retCanonicalPathName,
	char far *retExpandedPathName);
```
**Description :**

This function takes a database handle (DBHANDLE) and returns canonical and/or 
expanded path specifications.

**Parameters :**
Input :
hDB  -  A handle to a Domino database.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully got path specifications for database.


retCanonicalPathName  -  The address of a text buffer that in which the canonical pathname for the Domino database associated with hDB is returned.   The pathname is returned as a null-terminated LMBCS string.   The buffer should be declared with a length of MAXPATH.    If NULL is provided, nothing is returned.  

A canonical pathname is a pathname that is relative to the Domino or  Data Directory, and is not fully qualified (does not have a drive letter, etc).  It is useful for comparing 2 different database handles to see if they refer to the same file, since no matter what file name the user provided, the canonical pathname will always be returned as a relative pathname.

retExpandedPathName  -  The address of a text buffer in which the expanded pathname for the Domino database associated with hDB is returned.  The pathname is returned as a null-terminated LMBCS string.  The buffer should be declared with a length of MAXPATH.  If NULL is provided, nothing is returned.

For a remotely accessed database located on a Lotus Domino Server, the expanded pathname is the same as the canonical pathname.  If the database is located on the same machine as the API program, the expanded pathname consists of a physical or redirected drive letter, all directories required to reach the Domino database, the filename and the appropriate database class extension suffixed.


**Sample Usage :**
```
 
   /* Output PATH and ID info on both Dbs */
  
 if (error_status = NSFDbPathGet(db_handle_src,
                                   src_canonicalpath,
                                   src_expandedpath))
       goto Exit;

   printf("Canonical Path of SRC   = %s\n", src_canonicalpath);
   printf("Expanded Path of SRC        = %s\n", src_expandedpath);

```
**See Also :**
[NSFDbLocateByReplicaID](/domino-c-api-docs/reference/Func/NSFDbLocateByReplicaID)
[NSFDbOpen](/domino-c-api-docs/reference/Func/NSFDbOpen)
[NSFDbOpenExtended](/domino-c-api-docs/reference/Func/NSFDbOpenExtended)
[OSPathNetConstruct](/domino-c-api-docs/reference/Func/OSPathNetConstruct)
[OSPathNetParse](/domino-c-api-docs/reference/Func/OSPathNetParse)
---
