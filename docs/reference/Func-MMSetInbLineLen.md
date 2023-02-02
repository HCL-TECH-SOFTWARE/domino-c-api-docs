##### Function : MIME
##### MMSetInbLineLen - set Conversion Controls 'inbound line length' setting
---
##### #include <mailmisc.h>
void LNPUBLIC **MMSetInbLineLen(**

	CCHANDLE  hCC,
	WORD  wInbLineLen);
**Description :**
The function  MMSetInbLineLen sets the Conversions Controls 'inbound line 
length' setting to the input value, wInbLineLen.  No checking is done for out 
of bounds values.
**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

wInbLineLen  -  the value to use for the Conversion Controls 'inbound line length' setting.

Output :
(routine)  -  void


**Sample Usage :**
```
MMSetInbLineLen(hCC, 75); /* if set, when converting MIME rich text parts 
(i.e., text/html) to CD, justify using */
	   /*  this right margin.  (text/plain parts are never justified) 
(default is 75) *

```
**See Also :**
[MMGetInbLineLen](D:/md_files/MMGetInbLineLen.md)
[CCHANDLE](D:/md_files/CCHANDLE.md)
---
