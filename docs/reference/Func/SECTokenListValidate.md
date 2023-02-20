##### Function : SSO
##### SECTokenListValidate - Find the preferred token in the list and validate it
---
```
#include <bsafe.h>
STATUS LNPUBLIC SECTokenListValidate(

	char *ServerName,
	char *OrgName,
	char *ConfigName,
	SSO_LTPA_TOKEN_LIST *pTokenList,
	SSO_LTPA_TOKEN_LIST **retpValidatedToken,
	DWORD  dwRequestedInfoFlags,
	SSO_TOKEN_INFO_DESC *retpInfo,
	SSO_LTPA_TOKEN_LIST **retpCompatibilityToken,
	DWORD  dwReserved,
	void *vpReserved);
```
**Description :**

Validate the input Single Sign-On token list. The list can contain one or more 
tokens. This routine will find the preferred token in the list and attempt to 
validate it. If a token validation is not successful, the routine will 
investigate other tokens in the list to find one which can be validated.  On 
success, a pointer to the validated token is returned in retpValidatedToken. 
After a token in the list is successfully validated, the rest of the list may 
be ignored. 

The routine can return detailed information about the token which has been 
validated.  The info returned will be the info from the token pointed to by the 
returned retpValidatedToken, which is, according to the configuration, the 
preferred token in the list.  If the caller wants to validate each token 
individually, the caller should use SECTokenValidate2 instead for each token 
(because this routine only returns results for the preferred token in the list).

The caller can request information about the validated token to be returned in 
retpInfo struct. If retpInfo is non-null, then the retpInfo will always contain 
this output:
   TokenType -- currently either SECTOKENFORMAT_LTPATOKEN or 
SECTOKENFORMAT_LTPATOKEN2
   Expiration
   Creation (if Domino format token)
Optional output is requested by setting the dwRequestedInfoFlags.  Currently 
supported flags:
  SECTOKEN_RETURN_USERNAME - return the name of the user whom this token 
represents.
  SECTOKEN_RETURN_RAWTOKENUSERNAME - return the user name exactly as it appears 
in the token.
  SECTOKEN_RETURN_ATTRIBUTE_LIST - return the attribute list contained in an 
LtpaToken2 token.
  SECTOKEN_RETURN_RENEWAL_TIME - return renewal information that may apply in 
Domino-only configurations supporting idle session timeout.  A pointer to the 
renewal timedate is returned in retpInfo->vpReservedTiming. 

If dwRequestedInfoFlags is non-zero, the caller must free the resources 
associated with the output retpInfo by calling SECTokenFreeInfo().

For WebSphere-compatible SSO configurations, the SSO configuration may specify 
the use of both LtpaToken and LtpaToken2 (sometimes referred to as 
compatibility mode).  This routine can check for the existence of both of these 
tokens.  If one token type is in the token list, but the other token type is 
not in the list, the caller can request the routine to create the missing token 
type (i.e. the compatibility token). The caller can request a compatibility 
token in retpCompatibilityToken, which would be returned only if the 
configuration is in compatibility mode and if the pTokenList does not already 
contain both LtpaToken and LtpaToken2. If a compatibility token is returned, it 
must be freed by the caller using SECTokenListFree().

**Parameters :**
Input :
ServerName  -  Domino server to ask to validate the token. (Reserved as NULL)

OrgName  -  Organization that the server belongs to (OPTIONAL: Specify NULL if not using 'Internet Sites' view for configuration)

ConfigName  -  Name of Web SSO Configuration to use.

pTokenList  -  the list of tokens on which validation should be attempted.  For example, LtpaToken may be detected in the HTTP stream.  LtpaToken can be converted into an entry in a token list by calling SECCreateTokenListEntry().

dwRequestedInfoFlags  -  (optional)see long description for information about the flags

dwReserved  -  Must be 0, for future use

Output :
(routine)  -  Return status from this call.
	NOERROR - success
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


retpValidatedToken  -  pointer to which of the tokens in the list has been successfully validated. Note that info for this token entry in the list may be updated during the course of this call if the token entry was previously of unknown type (tokenType updated), or if SSO_TOKEN info (name, domainlist, domainnum) was unspecified in the callers list entry.

retpInfo  -  (optional) Return additional token information about the validated token in the token list into the callers SSO_TOKEN_INFO_DESC struct. To prepare for the receiving of information in the callers struct, the callers struct should be initialized, storing zero in all fields.  See detailed description for options and information about freeing allocated resources. 

retpCompatibilityToken  -  (optional).  Location to return a compatibility token, which must be freed by the caller using SECTokenListFree(). see long description for compatibility token information

vpReserved  -  must be NULL, for future use


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
	NULL, /* no compatibility token needed */
	0, NULL))
	goto Done;

/* The token in the token list that was successfully validated is now pointed 
to by pValidatedToken. */

/* The validated token contains a user name that we asked to be returned in 
Info.Username.ptr */

/* Were done with using the detailed token info so free it. */
SECTokenFreeInfo( &Info, TRUE, 0 );
```
**See Also :**
[SECCreateTokenListEntry](/reference/Func/SECCreateTokenListEntry)
[SECTokenValidate](/reference/Func/SECTokenValidate)
[SECTokenValidate2](/reference/Func/SECTokenValidate2)
[SSO_LTPA_TOKEN_LIST](/reference/Data/SSO_LTPA_TOKEN_LIST)
[SSO_TOKEN_INFO_DESC](/reference/Data/SSO_TOKEN_INFO_DESC)
---
