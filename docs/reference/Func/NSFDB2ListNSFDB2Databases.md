##### Function : Database
##### NSFDB2ListNSFDB2Databases - Provides a list of all NSFDB2 databases.  
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDB2ListNSFDB2Databases(

	MEMHANDLE *hDbList,
	void far **pDbList,
	const char far *tablespaceName);
```
**Description :**

Provides a list of all NSFDB2 databases.  An NSFDB2 database is a database that 
you can work with in DB2 and in Notes/Domino.

**Parameters :**
Input :

tablespaceName  -  (optional):   Limits results to NSFDB2 databases in this tablespace.  Passing NULL will result in a list of all NSFDB2 databases served by Domino.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successful.

ERR_DB2NSF_NOT_ENABLED_FOR_DB2 - The Domino server is not enabled for DB2.

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


hDbList  -  Address of a HANDLE in which the handle to the Domino memory object containing the newly created text LIST is returned.   The list will contain a file path of all NSFDB2 databases served by Domino.  Upon successful return, the list memory object is locked and a pointer to the object is returned in pDbList.  Since the object is returned locked, you must explicitly unlock the object (OSUnlockObject) before attempting to free it (OSMemFree). 
Use ListGetText(*pDbList, FALSE, EntryNumber, ....) to obtain each NSFDB2 database file path.

pDbList  -  Pointer to the newly created list of bad link file names.


**Sample Usage :**
```
        MEMHANDLE      hDbList;
 void   far  *pDbList;
 STATUS      rc;
 char        *pEntry;
 WORD        len;

 rc = NSFDB2ListNSFDB2Databases(&hDbList, &pDbList, NULL);
 /* get the first NSFDB2 database */
 for (int x=0; x < ListGetNumEntries(hDbList, FALSE); x++)
 {

	if ( (ListGetText(pDbList, FALSE, x, *pEntry, &len)) == NOERROR)
	{
	 printf("%s\n", )
	}
 }
 OSUnlockObject(hDbList);
 OSMemFree(hDbList);
```
**See Also :**
[ListGetText](/reference/Func/ListGetText)
[NSFDB2GetInfo](/reference/Func/NSFDB2GetInfo)
[NSFDB2GetServerInfo](/reference/Func/NSFDB2GetServerInfo)
[NSFDB2ReconnectNotesDatabase](/reference/Func/NSFDB2ReconnectNotesDatabase)
[NSFDB2RegenerateLinks](/reference/Func/NSFDB2RegenerateLinks)
---
