##### Function : Database
##### NSFDbModifiedTime - Get a database's data/non-data last modified times.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbModifiedTime(

	DBHANDLE  hDB,
	TIMEDATE far *retDataModified,
	TIMEDATE far *retNonDataModified);
```
**Description :**

This function obtains the time/date of the last modified data and non-data 
notes in the specified database.  The same information can also be obtained 
with NSFDbOpenExtended.

**Parameters :**
Input :
hDB  -  A handle to a Domino database.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully obtained the database's data and non-data last modified times.

ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


retDataModified  -  The address of a TIMEDATE structure in which the last modified time/date of the most recently modified data note/document is returned.

retNonDataModified  -  The address of a TIMEDATE structure in which the last modified time/date of the most recently modified non-data note/document is returned.


**Sample Usage :**
```

   /* Get Last modified time/date for data and non-data notes */

   if (error_status = NSFDbModifiedTime(db_handle_dst, &data_td_dst,
                                        &nondata_td_dst))
       goto Exit;

```
**See Also :**
[NSFDbOpenExtended](/reference/Func/NSFDbOpenExtended)
[OSCurrentTIMEDATE](/reference/Func/OSCurrentTIMEDATE)
[TimeDateAdjust](/reference/Func/TimeDateAdjust)
---
