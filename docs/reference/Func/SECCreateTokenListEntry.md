##### Function : SSO
##### SECCreateTokenListEntry - Allocate a new entry that can be inserted into a Single Sign-On  token list.
---
```
#include <bsafe.h>
STATUS LNPUBLIC SECCreateTokenListEntry(

	SECTOKENFORMAT  TokenType,
	char *pToken,
	char *pTokenName,
	char *pDomainList,
	WORD  wNumDomains,
	BOOL  bSecureOnly,
	SSO_LTPA_TOKEN_LIST **retpEntry,
	DWORD  dwReserved,
	void *vpReserved);
```
**Description :**

Allocate a new entry that can be inserted into a Single Sign-On  token list.  
The entry will usually just be storing a token that may need to be validated, 
therefore it is optional to provide domain info settings etc associated with a 
browser cookie.

**Parameters :**
Input :
TokenType  -  one of SECTOKENFORMAT_LTPATOKEN, SECTOKENFORMAT_LTPATOKEN2, SECTOKENFORMAT_UNKNOWN

pToken  -  a locked pointer to the token

pTokenName  -  a locked pointer to the token name, e.g. cookie name such as LtpaToken (can be NULL)

pDomainList  -  locked pointer (always one domain only), or NULL

wNumDomains  -  if non-zero, should currently always be 1

bSecureOnly  -  currently always set to FALSE, for future use

dwReserved  -  Must be 0, for future use.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


retpEntry  -  location to store newly allocated entry.  Caller is responsible to free using SECTokenListFree()

vpReserved  -  should be NULL, for future use


**Sample Usage :**
```
STATUS error = NOERROR;
SSO_LTPA_TOKEN_LIST *pTokenEntry = NULL;

if (error = SECCreateTokenListEntry( 
  SECTOKENFORMAT_LTPATOKEN, 
  pLtpaData, /* pointer to the LtpaToken found in HTTP cookie */ 
  NULL, NULL, 0, FALSE, 
  &pTokenEntry, 
  0, NULL ))
  goto Done;

/* Now do something with the returned pTokenEntry, e.g. validate it by calling 
SECTokenListValidate()  */


/* Free when done with the entry */
SECTokenListFree ( &pTokenEntry, 0, NULL );
```
**See Also :**
[SECTOKENFORMAT](/reference/Data/SECTOKENFORMAT)
[SECTokenListGenerate](/reference/Func/SECTokenListGenerate)
[SECTokenListValidate](/reference/Func/SECTokenListValidate)
[SSO_LTPA_TOKEN_LIST](/reference/Data/SSO_LTPA_TOKEN_LIST)
---
