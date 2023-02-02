##### Function : SSO
##### SECTokenValidate2 - Validate an SSO token
---
##### #include <bsafe.h>
STATUS LNPUBLIC **SECTokenValidate2(**

	char *ServerName,
	char *OrgName,
	char *ConfigName,
	char *TokenData,
	SECTOKENFORMAT  AssumedType,
	DWORD  dwRequestedInfoFlags,
	SSO_TOKEN_INFO_DESC *retpInfo,
	DWORD  dwReserved,
	void *vpReserved);
**Description :**
Validate an SSO token.

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
**Parameters :**
Input :
ServerName  -  Domino server to ask to validate the token. (Reserved as NULL)

OrgName  -  Organization that the server belongs to (OPTIONAL: Specify NULL if not using 'Internet Sites' view for configuration)

ConfigName  -  Name of Web SSO Configuration to use.

TokenData  -  the SSO token to be validated (e.g. may be the value associated with an HTTP cookie named “LtpaToken” or a cookie named “LtpaToken2”)

AssumedType  -  The caller gives information about what type of token is being validated.  If the token has been received in an HTTP cookie, the AssumedType of token would be evident to the caller based on the name of the cookie (LtpaToken vs LtpaToken2). AssumedType can be set to SECTOKENFORMAT_UNKNOWN, however this may negatively impact performance.  If the routine does not know the type of the token it is validating, it will try to validate the token as any of the allowed token types in the configuration.

dwRequestedInfoFlags  -  (optional) see detailed description

dwReserved  -  Must be 0, for future use

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

    NOERROR - Successful.

    ERR_xxx - Errors returned by lower level functions.  Call OSLoadString to interpret the error code for display.


retpInfo  -  (optional) Return additional token information about the validated token in the token list into the caller’s SSO_TOKEN_INFO_DESC struct. To prepare for the receiving of information in the caller’s struct, the caller’s struct should be initialized, storing zero in all fields.  See detailed description for options and information about freeing allocated resources. 

vpReserved  -  should be NULL, for future use  

**Sample Usage :**
```
STATUS error = NOERROR;
SSO_TOKEN_INFO_DESC Info = {0};

/* Try to validate an LtpaToken2 token, e.g. a token found in an HTTP 
LtpaToken2 cookie. */
if (error = SECTokenValidate2(
	NULL,
	pOrgName,
	pConfigName, 
	pTokenData, /* LtpaToken2 */
	SECTOKENFORMAT_LTPATOKEN2,
	SECTOKEN_RETURN_USERNAME, 
	&Info,
	0,
	NULL
	))
  goto Done;

/* The validated token contains a user name that we asked to be returned in 
Info.Username.ptr */

/* We’re done with using the detailed token info so free it. */
SECTokenFreeInfo( &Info, TRUE, 0 );
```
**See Also :**
[SECTOKENFORMAT](D:/md_files/SECTOKENFORMAT.md)
[SECTokenListValidate](D:/md_files/SECTokenListValidate.md)
[SECTokenValidate](D:/md_files/SECTokenValidate.md)
[SSO_TOKEN_INFO_DESC](D:/md_files/SSO_TOKEN_INFO_DESC.md)
---
