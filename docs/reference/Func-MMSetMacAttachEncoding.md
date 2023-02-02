##### Function : MIME
##### MMSetMacAttachEncoding - set Conversion Controls 'Mac attachment encoding' setting.
---
##### #include <mailmisc.h>
void LNPUBLIC **MMSetMacAttachEncoding(**

	CCHANDLE  hCC,
	WORD  wMacAttachEncoding);
**Description :**
The function  MMSetMacAttachEncoding sets the Conversions Controls 'Mac 
attachment encoding' setting to the input value, wMacAttachEncoding.  No 
checking is done for out of bounds values.
**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

wMacAttachEncoding  -  the value to use for the Conversion Controls 'Mac attachment encoding' setting.

Output :
(routine)  -  void


**Sample Usage :**
```
MMSetMacAttachEncoding(hCC, 0); /* CD to MIME conversion */
	    /* 1 - MultiPart/AppleDouble (default) */
	    /* 2 - Application/Mac-BinHex40 */

```
**See Also :**
[MMGetMacAttachEncoding](D:/md_files/MMGetMacAttachEncoding.md)
[CCHANDLE](D:/md_files/CCHANDLE.md)
---
