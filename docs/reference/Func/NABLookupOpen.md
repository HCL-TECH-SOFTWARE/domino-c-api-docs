##### Function : Name & Address Book
##### NABLookupOpen - Prepare to do directory lookup operations by creating a NABLookup object.
---
```
#include <nlookup.h>
STATUS LNPUBLIC NABLookupOpen(

	void **retpNABLookup,
	DWORD  dwReserved,
	void *vpReserved);
```
**Description :**

Prepare to do directory lookup operations by creating a NABLookup object.  For 
example, call NABLookupOpen() in order to prepare for calling 
NABLookupAuthenticatedUser(), which takes a NABLookup object as an input 
parameter.  If NABLookupOpen() succeeds, the caller should eventually call 
NABLookupClose() to free resources.

**Parameters :**
Input :

dwReserved  -  Must be 0, for future use.

Output :
(routine)  -  Return status from this call.
	NOERROR - Success.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


retpNABLookup  -  location where a pointer to a NABLookup object can be stored.

vpReserved  -  Must be NULL, for future use.


**Sample Usage :**
```
void *pNABLookup = NULL;
STATUS error = NABLookupOpen (&pNABLookup, 0, NULL);

if (error)
  goto Done;
```
**See Also :**
[NABLookupAuthenticatedUser](/domino-c-api-docs/reference/Func/NABLookupAuthenticatedUser)
[NABLookupClose](/domino-c-api-docs/reference/Func/NABLookupClose)
---
