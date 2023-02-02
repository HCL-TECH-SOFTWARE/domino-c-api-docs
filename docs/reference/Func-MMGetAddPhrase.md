##### Function : MIME
##### MMGetAddPhrase - get Conversion Controls 'add phrase' setting
---
##### #include <mailmisc.h>
WORD LNPUBLIC **MMGetAddPhrase(**

	CCHANDLE  hCC);
**Description :**
The function  MMGetAddPhrase returns the Conversions Controls 'add phrase' 
setting.
**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  0/1 - no phrase added or removed,
              2   - add abbreviated DN,
              3   - add alt name if it exists else DN,
              4   - Remove all phrases and comments (default 0)


**Sample Usage :**
```
WORD wAddPhrase;

wAddPhrase = MMGetAddPhrase(hCC);

```
**See Also :**
[CCHANDLE](D:/md_files/CCHANDLE.md)
[MMSetAddPhrase](D:/md_files/MMSetAddPhrase.md)
---
