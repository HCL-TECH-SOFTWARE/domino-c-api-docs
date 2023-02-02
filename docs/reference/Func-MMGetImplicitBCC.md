##### Function : MIME
##### MMGetImplicitBCC - get Conversion Controls 'implicit BCC' setting.
---
##### #include <mailmisc.h>
BOOL LNPUBLIC **MMGetImplicitBCC(**

	CCHANDLE  hCC);
**Description :**
The function  MMGetImplicitBCC returns the Conversions Controls 'implicit BCC' 
setting.
**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  if TRUE, add a BCC for every recipient not listed in a To, CC, or Bcc header when importing (default FALSE)


**Sample Usage :**
```
BOOL bImplicitBCC;

bImplicitBCC = MMGetImplicitBCC(hCC);

```
**See Also :**
[CCHANDLE](D:/md_files/CCHANDLE.md)
[MMSetImplicitBCC](D:/md_files/MMSetImplicitBCC.md)
---
