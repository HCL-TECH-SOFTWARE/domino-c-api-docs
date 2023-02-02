##### Function : Database
##### NSFDbSpaceUsage - Returns information about the usage of space in a database.
---
##### #include <nsfdb.h>
STATUS LNPUBLIC **NSFDbSpaceUsage(**

	DBHANDLE  hDB,
	DWORD far *retAllocatedBytes,
	DWORD far *retFreeByes);
**Description :**
This function returns the number of bytes allocated and the number of bytes 
free in a specified database.

The total size of  the number of bytes allocated plus the number of bytes free 
will differ from the file system size of the database.  This is due to internal 
rounding of the size up to the next 256K boundary.  Used and unused space is 
also calculated in "chunks" of allocation granularity while the file system 
size is determined in actual bytes.

The percent of the database that is in use is the result of the number of bytes 
allocated divided by the size of the database, multiplied by 100.
**Parameters :**
Input :
hDB  -  Handle to the database.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - success

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that  it is best to use the code in a call to OSLoadString and display/log the error for the user.


retAllocatedBytes  -  Pointer to the returned number of bytes allocated in the database for data notes, form notes, view notes, etc.

retFreeByes  -  Pointer to the returned number of bytes free in the database.

**Sample Usage :**
```

  DBHANDLE hNotesDB;
  DWORD dwUsed;
  DWORD dwFree;
  STATUS error;
  
  /* code to open the database goes here */
  ...

  error = NSFDbSpaceUsage (hNotesDB, &dwUsed, &dwFree);

  if (error != NOERROR)
  {
     NSFDbClose (hNotesDB);
     return (ERR(error));
  }

  printf(
     "Allocated:  %10lu;\t  Free:  %10lu;\t  In Use:  %10.2f%s",
     dwUsed, dwFree, (float)dwUsed / (float)(dwFree + dwUsed) * 100, "%");

```
**See Also :**
[](D:/md_files/.md)
---
