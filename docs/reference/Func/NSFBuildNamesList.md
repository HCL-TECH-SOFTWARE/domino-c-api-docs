##### Function : Access Control List
##### NSFBuildNamesList - Builds a NAMES_LIST structure.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFBuildNamesList(

	char *UserName,
	DWORD  dwFlags,
	DHANDLE *rethNamesList);
```
**Description :**

This function builds a NAMES_LIST structure with the supplied UserName, and 
returns a HANDLE to the structure.  The resulting NAMES_LIST structure contains 
the UserName along with any related group names the user is a member of.  Group 
information is obtained from the local Domino Directory.

This HANDLE may then be passed to the function NSFDbOpenExtended to open a 
local database with the specified UserName.  This causes the user's ACL 
permissions to be enforced if they exist in the Access Control List.  Normally 
Domino and Notes do not check the ACL when opening a local database.

After calling NSFBuildNamesList, you must set the Authenticated member of the 
NAMES_LIST structure to NAMES_LIST_AUTHENTICATED or 
NAMES_LIST_PASSWORD_AUTHENTICATED (or both values OR'd together) to gain access 
to the database.  Any other value will result in the error code ERR_NOACCESS 
being returned.

**Parameters :**
Input :
UserName  -  The specified user name whose ACL you want enforced.  Use NULL for the current User.  If the user name is hierarchical, use the fully distinguished name, not the abbreviated user name.

dwFlags  -  Currently not used.  Set to 0.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - Successfully built the NAMES_LIST.
ERR_NO_ACCESS - User isn't authorized to perform operation.
ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


rethNamesList  -  Returns a HANDLE to a NAMES_LIST structure that contains the UserName along with any related group names the user is a member of. The caller is responsible for freeing this handle with OSMemFree.  This structure is defined in ACL.H.


**Sample Usage :**
```
if (error = NSFBuildNamesList(pUserName, 0 ,&hNamesList))
   goto Exit;

pNamesList = OSLock(NAMES_LIST, hNamesList);

/* set Authenticated member of NAMES_LIST structure */
pNamesList->Authenticated = NAMES_LIST_AUTHENTICATED | 
NAMES_LIST_PASSWORD_AUTHENTICATED;

/* to print out NAMES_LIST structure */
ptr = (char *)&pNamesList[1];

for (i=0; i<pNamesList->NumNames; i++)
{
  printf("Names:%s\n", ptr);
  ptr += strlen(ptr) + 1;
}


/* pass hNamesList to NSFDbOpenExtended */
error = NSFDbOpenExtended(PathName, 0, hNamesList, 0, &db_handle, data_td_src,
                          nondata_td_src);

/* free up memory */
if (hNamesList)
{
  OSUnlock(hNamesList);
  OSMemFree(hNamesList);
}
if (error)
	...
```
**See Also :**
[NAMES_LIST](/domino-c-api-docs/reference/Data/NAMES_LIST)
[NAMES_LIST_xxx](/domino-c-api-docs/reference/Symb/NAMES_LIST_xxx)
[NSFDbOpenExtended](/domino-c-api-docs/reference/Func/NSFDbOpenExtended)
---
