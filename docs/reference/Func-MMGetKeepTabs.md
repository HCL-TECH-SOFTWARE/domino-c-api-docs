##### Function : MIME
##### MMGetKeepTabs - get Conversion Controls 'keep tabs' setting
---
##### #include <mailmisc.h>
BOOL LNPUBLIC **MMGetKeepTabs(**

	CCHANDLE  hCC);
**Description :**
The function  MMGetKeepTabs returns the Conversions Controls 'keep tabs' 
setting.
**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  if TRUE, when converting CD to MIME Stream, don't convert tabs to spaces (default is FALSE)


**Sample Usage :**
```
BOOL bKeepTabs;

bKeepTabs = MMGetKeepTabs(hCC);

```
**See Also :**
[CCHANDLE](D:/md_files/CCHANDLE.md)
[MMSetKeepTabs](D:/md_files/MMSetKeepTabs.md)
---
