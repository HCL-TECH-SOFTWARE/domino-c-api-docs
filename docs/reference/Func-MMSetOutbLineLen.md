##### Function : MIME
##### MMSetOutbLineLen - set Conversion Controls 'outbound line length' setting
---
##### #include <mailmisc.h>
void LNPUBLIC **MMSetOutbLineLen(**

	CCHANDLE  hCC,
	WORD  wOutbLineLength);
**Description :**
The function  MMSetOutbLineLen sets the Conversions Controls 'outbound line 
length' setting to the input value, wOutbLineLength.  No checking is done for 
out of bounds values.
**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

wOutbLineLength  -  the value to use for the Conversion Controls 'outbound line length' setting.

Output :
(routine)  -  void


**Sample Usage :**
```
MMSetOutbLineLen(hCC, 75); /* if set, when convert CD to MIME, justify using 
this right margin (default is 75) */
```
**See Also :**
[MMGetOutbLineLen](D:/md_files/MMGetOutbLineLen.md)
[CCHANDLE](D:/md_files/CCHANDLE.md)
---
