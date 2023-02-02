##### Function : MIME
##### MMGetResent - get Conversion Controls 'support resent headers' setting
---
##### #include <mailmisc.h>
BOOL LNPUBLIC **MMGetResent(**

	CCHANDLE  hCC);
**Description :**
The function  MMGetResent returns the Conversions Controls 'support resent 
headers' setting.
**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  if TRUE support Resent-XXX headers when importing (default is FALSE)


**Sample Usage :**
```
BOOL bSupportResent;

bSupportResent = MMGetResent(hCC);

```
**See Also :**
[CCHANDLE](D:/md_files/CCHANDLE.md)
[MMSetResent](D:/md_files/MMSetResent.md)
---
