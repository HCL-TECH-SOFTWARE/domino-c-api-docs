##### Function : SSO
##### SECTokenFreeInfo - Free information returned about a specific SSO token by SECTokenListGenerate(), SECTokenListValidate(), SECTokenValidate2()
---
```
#include <bsafe.h>
void LNPUBLIC SECTokenFreeInfo(

	SSO_TOKEN_INFO_DESC *pInfo,
	BOOL  bFreeAll,
	DWORD  dwRequestedInfoFlags);
```
**Description :**

Free information returned about a specific SSO token by SECTokenListGenerate(), 
SECTokenListValidate(), SECTokenValidate2().  The respective token routine may 
have dynamically allocated memory in order to return detailed information about 
a token, and the SECTokenFreeInfo() routine ensures that this associated memory 
is freed.  The callers input struct may contain a variety of items.  If the 
caller wishes to specify which items should be freed and which should not be 
freed (perhaps some items the caller has longterm use for and will free later), 
the caller can pass in flags to declare which items should be freed. After 
memory has been freed, the pointers in the callers struct may become 
re-initialized to NULL.

**Parameters :**
Input :
pInfo  -  A pointer to the callers struct that was passed to a token routine for returning more detailed information about a token.

bFreeAll  -  If TRUE, then free all allocated items in the pInfo struct.

dwRequestedInfoFlags  -  If bFreeAll is FALSE, then only free those items associated with flags passed in.  Flags may be SECTOKEN_RETURN_USERNAME
SECTOKEN_RETURN_RAWTOKENUSERNAME
SECTOKEN_RETURN_ATTRIBUTE_LIST
SECTOKEN_RETURN_RENEWAL_TIME

Output :
(routine)  -  None.



**Sample Usage :**
```
STATUS error = NOERROR;
SSO_LTPA_TOKEN_LIST *pValidatedToken = NULL;
SSO_TOKEN_INFO_DESC Info = {0};

if (error = SECTokenListValidate( NULL,
      pOrgName,
	pCfgName,
	pTokenList,
	&pValidatedToken,
	SECTOKEN_RETURN_USERNAME, 
	&Info,
	NULL, 0, NULL))
	goto Done;

/* The token in the token list that was successfully validated is now pointed 
to by pValidatedToken. */

/* The validated token contains a user name that we asked to be returned in 
Info.Username.ptr */

/* Were done with using the detailed token info so free it. */
SECTokenFreeInfo( &Info, TRUE, 0 );
```
**See Also :**
[SECTokenListGenerate](/domino-c-api-docs/reference/Func/SECTokenListGenerate)
[SECTokenListValidate](/domino-c-api-docs/reference/Func/SECTokenListValidate)
[SECTokenValidate2](/domino-c-api-docs/reference/Func/SECTokenValidate2)
[SSO_TOKEN_INFO_DESC](/domino-c-api-docs/reference/Data/SSO_TOKEN_INFO_DESC)
[SSO_TOKEN_ITEM](/domino-c-api-docs/reference/Data/SSO_TOKEN_ITEM)
---
