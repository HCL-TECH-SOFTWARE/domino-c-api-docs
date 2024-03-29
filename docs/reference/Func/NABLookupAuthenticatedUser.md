##### Function : Name & Address Book
##### NABLookupAuthenticatedUser - Lookup an authenticated user in the directory.
---
```
#include <nlookup.h>
STATUS LNPUBLIC NABLookupAuthenticatedUser(

	void *pNABLookup,
	char *orgName,
	char *user,
	DWORD  flags,
	NABLOOKUP_RECORD *pRetNabLookupRecord,
	DWORD  dwNablookupRecordSize,
	DWORD  dwReserved,
	void *vpReserved);
```
**Description :**

Lookup an authenticated user in the directory.  This routine should only be 
called if the user has already been authenticated by some external mechanism, 
e.g. user is authenticated by SSO LtpaToken, by web connection header, by DSAPI 
callout, etc. Because the user has already been authenticated, this routine 
does not involve verifying the user's password.  The lookup will always be done 
in the $Users view of the directory.

**Parameters :**
Input :
pNABLookup  -  a NABLookup object has been created by NABLookupOpen() 

orgName  -  organization name for Internet sites configuration (can be NULL)

user  -  distinguished name of the user to lookup (i.e. should not be "Anonymous", and should not be a shortname or other name which has not been mapped to a distinguished name)

flags  -  The flags value is fLookupAuthenticatedKerberosName or 0,indicates the user name is a Kerberos, or use 0

dwNablookupRecordSize  -  Size of the structure holding the results of a directory lookup.

dwReserved  -  Must be 0, for future use

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


pRetNabLookupRecord  -  the callers structure holds the results of a directory lookup for the user.  The results will be unusable after the caller invokes NABLookupClose().

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
 NABLookupClose( &pNABLookup,  &LookupEntry,  sizeof(NABLOOKUP_RECORD), 0, NULL 
);
	}
```
**See Also :**
[NABLookupClose](/domino-c-api-docs/reference/Func/NABLookupClose)
[NABLookupOpen](/domino-c-api-docs/reference/Func/NABLookupOpen)
---
