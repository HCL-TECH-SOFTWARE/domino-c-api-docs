##### Function : MIME
##### MMGetAddItems - get Conversion Controls 'add items' setting
---
##### #include <mailmisc.h>
char * LNPUBLIC **MMGetAddItems(**

	CCHANDLE  hCC);
**Description :**
The function  MMGetAddItems returns the Conversions Controls 'add items' 
setting.
**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  Comma delimited list of items names to preserve in msgs as they're exported (default is NULL)


**Sample Usage :**
```
char * pszAddItems;

pszAddItems = MMGetAddItems(hCC);

```
**See Also :**
[CCHANDLE](D:/md_files/CCHANDLE.md)
[MMSetAddItems](D:/md_files/MMSetAddItems.md)
---
