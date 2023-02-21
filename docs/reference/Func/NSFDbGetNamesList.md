##### Function : Access Control List
##### NSFDbGetNamesList - Returns a Handle to a NAMES_LIST structure.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbGetNamesList(

	DBHANDLE  hDB,
	DWORD  Flags,
	DHANDLE *rethNamesList);
```
**Description :**

This function is used with an Extension Manager running on a Lotus Domino 
server, and can be called after trapping an EM_NSFDBOPENEXTENDED hook.  This 
function returns a HANDLE to a NAMES_LIST structure which can be NULL (will 
always be NULL on a local database).  The NAMES_LIST structure contains ACL 
information for the specified database.  

Note: A database's ACL is only enforced on a server.


**Parameters :**
Input :
hDB  -  A Handle to a database.

Flags  -  The Flags parameter is not used at this time.  Set to 0.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully made the call.
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.



rethNamesList  -  Returns a HANDLE to a NAMES_LIST structure.   This structure is in the header file acl.h.  The handle may be NULL.


**Sample Usage :**
```
if (error = NSFDbGetNamesList(hDb, 0 ,&hNamesList))
   goto Exit;

/* to print out NAMES_LIST structure */
pNamesList = OSLock(NAMES_LIST, hNamesList);

ptr = (char *)&pNamesList[1];
for (i=0; i<pNamesList->NumNames; i++)
{
  printf("Names:%s\n", ptr);
  ptr += strlen(ptr) + 1;
}

/* free up memory */
if (hNamesList)
{
  OSUnlock(hNamesList);
  OSMemFree(hNamesList);
}

```
**See Also :**
[NAMES_LIST](/domino-c-api-docs/reference/Data/NAMES_LIST)
[NAMES_LIST_xxx](/domino-c-api-docs/reference/Symb/NAMES_LIST_xxx)
[NSFDbOpenExtended](/domino-c-api-docs/reference/Func/NSFDbOpenExtended)
---
