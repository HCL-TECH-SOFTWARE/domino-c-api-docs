##### Function : SSO
##### SECTokenListFree - Free all SSO tokens in the list created by SECTokenListGenerate()
---
```
#include <bsafe.h>
void LNPUBLIC SECTokenListFree(

	SSO_LTPA_TOKEN_LIST **pTokenList,
	DWORD  dwReserved,
	void *vpReserved);
```
**Description :**

Free all SSO tokens in the list created by SECTokenListGenerate().  The caller 
passes a pointer to where the token list is located.  After freeing the token 
list, the pointer to where the token list was located is reset to NULL.

**Parameters :**
Input :
pTokenList  -  pointer to where the token list is located.

dwReserved  -  Must be 0, for future use

Output :
(routine)  -  None


vpReserved  -  must be NULL, for future use.


**Sample Usage :**
```
STATUS error = NOERROR;
SSO_LTPA_TOKEN_LIST *pTokenList = NULL;

if( error = SECTokenListGenerate( NULL,
	pOrgName,
	pConfigName,
	pUserName,
      NULL, /* default creation time */
      NULL, /* default expiration time */
      NULL, /* no attributes */
      0, /* no optional flags */
      NULL, /* no optional return info */
      &pTokenList,
      0, NULL))
	goto Done;

SECTokenListFree( &pTokenList, 0, NULL );
```
**See Also :**
[SECTokenListGenerate](/reference/Func/SECTokenListGenerate)
[SSO_LTPA_TOKEN_LIST](/reference/Data/SSO_LTPA_TOKEN_LIST)
---
