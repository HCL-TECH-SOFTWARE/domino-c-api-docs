##### Function : MIME
##### MMSetInternetDomain - set Conversion Controls 'internet domain' setting
---
```
#include <mailmisc.h>
void LNPUBLIC MMSetInternetDomain(

	CCHANDLE  hCC,
	char *pszInternetDomain);
```
**Description :**

The function  MMSetInternetDomain sets the Conversions Controls 'internet 
domain' setting to the input value, pszInternetDomain.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

pszInternetDomain  -  the value to use for the Conversion Controls 'internet domain' setting.

Output :
(routine)  -  void



**Sample Usage :**
```
char *pszInternetDomain = "fqdn.com";

MMSetInternetDomain(hCC, pszInternetDomain); /* Local Internet Domain name used 
in Message-ID, 821 addresses (default is NULL) */

```
**See Also :**
[MMGetInternetDomain](/domino-c-api-docs/reference/Func/MMGetInternetDomain)
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
---
