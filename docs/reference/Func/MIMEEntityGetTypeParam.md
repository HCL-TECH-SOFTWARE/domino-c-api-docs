##### Function : MIME
##### MIMEEntityGetTypeParam - Get the string value and length of a MIME parameter for the input MIME entity.
---
```
#include <mimedir.h>
STATUS LNPUBLIC MIMEEntityGetTypeParam(

	PMIMEENTITY  pMIMEEntity,
	MIMESYMBOL  symParam,
	DHANDLE *phValue,
	DWORD *pdwValueLen);
```
**Description :**

This function MIMEEntityGetTypeParam returns a handle to the value of the input 
parameter, symParam, in the location pointed to by phValue.  It also returns 
the length of the parameter value in the location pointed to by pdwValueLen.  
The string is everything after the '='.  If the current entity does not contain 
the parameter indicated by symParam, MIMEEntityGetTypeParam returns the error 
ERR_MIME_NO_DATA.  If pMIMEEntity is NULL or if symParam is MIME_SYMBOL_UNKNOWN 
or MIME_SYMBOL_NONE, MIMEEntityGetTypeParam returns ERR_MISC_INVALID_ARGS.
  The caller is responsible for freeing the phValue memory.


**Parameters :**
Input :
pMIMEEntity  -  a pointer to current MIME entity.

symParam  -  the MIMESYMBOL for the desired parameter.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully accessed the MIMEDIRECTORY and allocated the parameter value memory.
	ERR_MISC_INVALID_ARGS - returned for various input parameter errors.
	ERR_MIME_NO_DATA - returned if the requested parameter is not found.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



phValue  -  a handle to an allocated block of memory containing the parameter value.

pdwValueLen  -  the length of the parameter value string in bytes.


**Sample Usage :**
```
HMIMEDIRECTORY hMIMEDir;
STATUS error;
PMIMEENTITY pRootEntity;
DHANDLE hParam;
DWORD dwParamLen;
const char *pszHeaderValue;

if (error = MIMEOpenDirectory(hNote, &hMIMEDir)) {
	goto exit;
}

if (error = MIMEGetRootEntity(hNote, &pRootEntity)) {
	goto exit;
}

if (error = MIMEEntityGetTypeParam(pRootEntity, MIME_SYMBOL_FILENAME, &hParam, 
&dwParamLen)) {
	goto exit;
}

if (error = MIMEFreeDirectory(hMIMEDir)) {
	goto exit;
}


```
**See Also :**
[MIMESYMBOL](/domino-c-api-docs/reference/Data/MIMESYMBOL)
[PMIMEENTITY](/domino-c-api-docs/reference/Data/PMIMEENTITY)
---
