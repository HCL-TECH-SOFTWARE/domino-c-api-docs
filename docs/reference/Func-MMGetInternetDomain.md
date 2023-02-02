##### Function : MIME
##### MMGetInternetDomain - get Conversion Controls 'internet domain' setting
---
##### #include <mailmisc.h>
char * LNPUBLIC **MMGetInternetDomain(**

	CCHANDLE  hCC);
**Description :**
The function  MMGetInternetDomain returns the Conversions Controls 'internet 
domain' setting.
**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  Local Internet Domain name used to construct Message-ID and 821 addresses (default is NULL)


**Sample Usage :**
```
char * pszInternetDomain;

pszInternetDomain = MMGetInternetDomain(hCC);


```
**See Also :**
[CCHANDLE](D:/md_files/CCHANDLE.md)
[MMSetInternetDomain](D:/md_files/MMSetInternetDomain.md)
---
