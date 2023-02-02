##### Function : SSO
##### SECTokenFreeInfo - Free information returned about a specific SSO token by SECTokenListGenerate(), SECTokenListValidate(), SECTokenValidate2()
---
##### #include <bsafe.h>
void LNPUBLIC **SECTokenFreeInfo(**

	SSO_TOKEN_INFO_DESC *pInfo,
	BOOL  bFreeAll,
	DWORD  dwRequestedInfoFlags);
**Description :**
Free information returned about a specific SSO token by SECTokenListGenerate(), 
SECTokenListValidate(), SECTokenValidate2().  The respective token routine may 
have dynamically allocated memory in order to return detailed information about 
a token, and the SECTokenFreeInfo() routine ensures that this associated memory 
is freed.  The caller’s input struct may contain a variety of items.  If the 
caller wishes to specify which items should be freed and which should not be 
freed (perhaps some items the caller has longterm use for and will free later), 
the caller can pass in flags to declare which items should be freed. After 
memory has been freed, the pointers in the caller’s struct may become 
re-initialized to NULL.
**Parameters :**
Input :
pInfo  -  A pointer to the caller’s struct that was passed to a token routine for returning more detailed information about a token.

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

/* We’re done with using the detailed token info so free it. */
SECTokenFreeInfo( &Info, TRUE, 0 );
```
**See Also :**
[SECTokenListGenerate](D:/md_files/SECTokenListGenerate.md)
[SECTokenListValidate](D:/md_files/SECTokenListValidate.md)
[SECTokenValidate2](D:/md_files/SECTokenValidate2.md)
[SSO_TOKEN_INFO_DESC](D:/md_files/SSO_TOKEN_INFO_DESC.md)
[SSO_TOKEN_ITEM](D:/md_files/SSO_TOKEN_ITEM.md)
---
