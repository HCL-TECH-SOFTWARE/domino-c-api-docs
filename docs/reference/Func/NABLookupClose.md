##### Function : Name & Address Book
##### NABLookupClose - Finish directory lookup operations by closing a NABLookup object. 
---
```
#include <nlookup.h>
void LNPUBLIC NABLookupClose(

	void **pNABLookup,
	void *pNabLookupRecord,
	DWORD  dwNablookupRecordSize,
	DWORD  dwReserved,
	void *vpReserved);
```
**Description :**

Finish directory lookup operations by closing a NABLookup object that was 
returned by a previous NABLookupOpen() call.  Optionally free resources 
associated with a NABLookup record that is holding the results of a directory 
lookup.

**Parameters :**
Input :
pNABLookup  -   location where a pointer to a NABLookup object has been stored by NABLookupOpen() 

pNabLookupRecord  -  (optional)pointer to the structure holding the results of a directory lookup which should be freed.

dwNablookupRecordSize  -  Size of the structure holding the results of a directory lookup.  Required if pNabLookupRecord is specified.

dwReserved  -  Must be 0, for future use

Output :
(routine)  -  None.


vpReserved  -  Must be NULL, for future use


**Sample Usage :**
```
void *pNABLookup = NULL;
NABLOOKUP_RECORD LookupEntry = {0};   
/* this is the struct that holds results of lookup */

STATUS error = NABLookupOpen( &pNABLookup, 0, NULL );
	
if (!error) {
	error = NABLookupAuthenticatedUser( pNABLookup,
	       pOrganizationName, /* set to NULL if none */
	                                    pUserDistinguishedName,
	                                    0,
	                                    &LookupEntry,
	                                    sizeof(NABLOOKUP_RECORD),
	                                    0,
	                                    NULL);

if (!error) {
	/* do whatever needs to be done with the user's info in LookupEntry 
struct */
	}

/* Free the resources, and zero out the LookupEntry struct */
 NABLookupClose( &pNABLookup, &LookupEntry, sizeof(NABLOOKUP_RECORD), 0, NULL );
	}
```
**See Also :**
[NABLookupAuthenticatedUser](/reference/Func/NABLookupAuthenticatedUser)
[NABLookupOpen](/reference/Func/NABLookupOpen)
---
