##### Function : MIME
##### MMGetMaxHops - get Conversion Controls 'maximum number of hops' setting
---
##### #include <mailmisc.h>
WORD LNPUBLIC **MMGetMaxHops(**

	CCHANDLE  hCC);
**Description :**
The function  MMGetMaxHops returns the Conversions Controls 'maximum number of 
hops' setting.
**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  Used to generate $Hops when importing (default is 25)


**Sample Usage :**
```
WORD wMaxHops;

wMaxHops = MMGetMaxHops(hCC);


```
**See Also :**
[CCHANDLE](D:/md_files/CCHANDLE.md)
[MMSetMaxHops](D:/md_files/MMSetMaxHops.md)
---
