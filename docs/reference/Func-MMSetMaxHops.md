##### Function : MIME
##### MMSetMaxHops - set Conversion Controls 'maximum number of hops' setting
---
##### #include <mailmisc.h>
void LNPUBLIC **MMSetMaxHops(**

	CCHANDLE  hCC,
	WORD  wMaxHops);
**Description :**
The function  MMSetMaxHops sets the Conversions Controls 'maximum number of 
hops' setting to the input value, wMaxHops.  No checking is done for out of 
bounds values.
**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

wMaxHops  -   the value to use for the Conversion Controls 'set maximum number of hops' setting.

Output :
(routine)  -  void


**Sample Usage :**
```
MMSetMaxHops(hCC, 25); /* Used to create $Hops when importing (default is 25) 
*/
```
**See Also :**
[MMGetMaxHops](D:/md_files/MMGetMaxHops.md)
[CCHANDLE](D:/md_files/CCHANDLE.md)
---
