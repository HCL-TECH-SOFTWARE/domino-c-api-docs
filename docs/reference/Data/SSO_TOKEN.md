##### Data Type : User Registration
##### SSO_TOKEN - Structure that defines a Single Sign-On token.
---
```
#include <bsafe.h>
```

**Definition :**

typedef struct{
	MEMHANDLE mhName;
	MEMHANDLE mhDomainList;
	WORD  wNumDomains;
	BOOL  bSecureOnly;
	MEMHANDLE mhData;
    } SSO_TOKEN;

**Description :**

This structure contains information representing an authentication token used for Single Sign-On. The typical use is to store this information in a browser 'cookie' for interoperability with Domino protocols that support Single Sign-On (IE: HTTP and DIIOP), as well as IBM WebSphere Advanced Server.
<ul><br>

<ul>mhName 	- MEMHANDLE to a null-terminated name for the token when set as a cookie. Access with OSMemoryLock.<br>
mhDomainList	- MEMHANDLE to a list of null-delimited DNS domains for the token when set as a cookie. Access with OSMemoryLock.<br>
wNumDomains	- Total number of domains contained in the mhDomainList member.<br>
bSecureOnly	- BOOL recommending that the token only be set on a secure connection.<br>
mhData		- MEMHANDLE to a the null-terminated token data.<br>
</ul>
See the Domino Administrators Guide for information on configuring Single Sign-On.</ul>



**See Also :**
[SECTokenFree](/domino-c-api-docs/reference/Func/SECTokenFree)
[SECTokenGenerate](/domino-c-api-docs/reference/Func/SECTokenGenerate)
[SECTokenValidate](/domino-c-api-docs/reference/Func/SECTokenValidate)
---
