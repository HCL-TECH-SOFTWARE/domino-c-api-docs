##### Function : Replica Info
##### NSFDbClearReplHistory - Clear database replication history
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbClearReplHistory(

	DBHANDLE  hDb,
	DWORD  dwFlags);
```
**Description :**

This function clears out the replication history information of the specified 
database replica.  This can also be done using the Notes user interface via the 
File/Replication/History menu item selection.

**Parameters :**
Input :
hDb  -  Handle to the database, already opened.

dwFlags  -  Must be zero.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully cleared replication history information.

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.



**Sample Usage :**
```
DBHANDLE    db_handle;         /* handle of source database */
   STATUS      error = NOERROR;   /* return status from API calls */
   char szErrorString[256];

   /* Open the database */
   ...

   /* Clear replication history */
   error = NSFDbClearReplHistory(db_handle, 0);
   if (error)
   {
      OSLoadString(0, ERR(error), szErrorString, 255);
      printf ("Error from NSFDbClearReplHistory:  %s\n\n", szErrorString);
      NSFDbClose (db_handle);
      LAPI_RETURN (ERR(error));      
   }
   printf ("Replication history cleared\n");

   /* Close the database */
   ...

```
**See Also :**
[NSFDbGetReplHistorySummary](/domino-c-api-docs/reference/Func/NSFDbGetReplHistorySummary)
---
