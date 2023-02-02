##### Function : Database
##### NSFDbModeGet - Check if DBHANDLE refers to database or a directory.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbModeGet(**

	DBHANDLE  hDB,
	USHORT far *retMode);
**Description :**
This function takes a DBHANDLE as input and returns a pointer to a USHORT that 
specifies whether the handle is associated with a database or with a 
directory.  It returns DB_LOADED in the specified USHORT if the DBHANDLE is a 
handle to a database or DB_DIRECTORY if the DBHANDLE is a handle to a directory.

Use this function to find out whether the DBHANDLE returned by NSFDbOpen() is a 
handle to a database or a handle to a directory.
**Parameters :**
Input :
hDB  -  The handle to the database or directory.

Output :
(routine)  -  Return status from this call.  A successful call returns NOERROR.


retMode  -  The address of a USHORT that receives the database mode, DB_LOADED or DB_DIRECTORY, as defined by DB_xxx (NSFDbModeGet).

**Sample Usage :**
```
if (Error = NSFDbModeGet (hDB, &usMode))
{
    fprintf (stderr, "Error: unable to get database mode.\n");
    return (ERR(Error));
}
if (usMode & DB_LOADED) /* hDB refers to a normal database file */
{
    ;                   /* this is what we expect: no output needed */
}
else if (usMode & DB_DIRECTORY) /* hDB refers to a directory  */
{
    fprintf (stderr, "Error: '%s' is a directory, not a file.\n",
                                szFilename);
    return (ERR(Error));
}
```
**See Also :**
[NSFDbOpen](D:/md_files/NSFDbOpen.md)
---
