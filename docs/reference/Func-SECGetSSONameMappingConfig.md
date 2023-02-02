##### Function : User Registration
##### SECGetSSONameMappingConfig - Get name mapping information from an SSO configuration Document.
---
##### #include <bsafe.h>
STATUS LNPUBLIC **SECGetSSONameMappingConfig(**

	char *ServerName,
	char *OrgName,
	char *ConfigName,
	BOOL *retbNameMapping,
	DWORD  dwReserved,
	void *vpReserved);
**Description :**
 This function gets name mapping information from an SSO configuration document 
if name mapping is turned on.
**Parameters :**
Input :
ServerName  -  Reserved, must be NULL.

OrgName  -  Optional.  Organization for internet site configuration.  Null if no organization name is desired.

ConfigName  -  Configuration name, usually "LtpaToken".

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is.


retbNameMapping  -  TRUE is SSO configuration document has name mapping enabled.

dwReserved  -  Reserved for future use.

vpReserved  -  Reserved for future use.

**See Also :**
[SECTokenGenerate](D:/md_files/SECTokenGenerate.md)
[SSO_TOKEN](D:/md_files/SSO_TOKEN.md)
---
