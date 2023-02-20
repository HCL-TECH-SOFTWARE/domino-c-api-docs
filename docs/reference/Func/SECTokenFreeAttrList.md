##### Function : SSO
##### SECTokenFreeAttrList - Free an attribute list
---
```
#include <bsafe.h>
void LNPUBLIC SECTokenFreeAttrList(

	SSO_LTPA2_ATTR **pAttrList,
	DWORD  dwReserved,
	void *vpReserved);
```
**Description :**

Free an attribute list associated with the LtpaToken2 type of token.  An 
LtpaToken2 token can have an attribute list included in the token to hold 
custom token data.   Some routines that encounter LtpaToken2 type of SSO tokens 
can return the list of attributes that have been found in LtpaToken2, for 
example an attribute list may be returned by SECTokenValidate2() or 
SECTokenListValidate() as part of detailed token information.  When 
SECTokenFreeAttrList() is called, the list is freed, and the location of the 
attribute list is reset to be NULL.

**Parameters :**
Input :
pAttrList  -  pointer to the location of the attribute list to free

dwReserved  -  Must be 0, for future use

Output :
(routine)  -  None


vpReserved  -  Must be NULL, for future use


**Sample Usage :**
```
STATUS error = NOERROR;
SSO_TOKEN_INFO_DESC Info = {0};
SSO_LTPA2_ATTR *pMyAttrList = NULL;

/* Try to validate an LtpaToken2 token, e.g. a token found in an HTTP 
LtpaToken2 cookie. */
if (error = SECTokenValidate2(
	NULL,
	pOrgName,
	pConfigName, 
	pTokenData, /* LtpaToken2 */
	SECTOKENFORMAT_LTPATOKEN2,
	SECTOKEN_RETURN_USERNAME | SECTOKEN_RETURN_ATTRIBUTE_LIST,
	&Info,
	0,
	NULL
	))
  goto Done;

/* The validated token contains a user name that we asked to be returned in 
Info.Username.ptr */

/* The validated token contains an LtpaToken2 attribute list that we asked to 
be returned in Info.AttributesList  */

/* Were done with using the detailed token info, except we want to keep the 
attribute list a little longer.  Free the username but keep the attribute list. 
*/
 
 pMyAttrList = Info.AttributesList;

 SECTokenFreeInfo( &Info, 
       FALSE,
       SECTOKEN_RETURN_USERNAME );
 
/* Now were done with the attributes list, so free it. */
SECTokenFreeAttrList (  &pMyAttrList, 0, NULL );    
```
**See Also :**
[SECTokenListGenerate](/reference/Func/SECTokenListGenerate)
[SECTokenListValidate](/reference/Func/SECTokenListValidate)
[SSO_LTPA2_ATTR](/reference/Data/SSO_LTPA2_ATTR)
---
