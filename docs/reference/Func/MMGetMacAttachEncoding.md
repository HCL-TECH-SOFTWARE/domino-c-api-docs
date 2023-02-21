##### Function : MIME
##### MMGetMacAttachEncoding - get Conversion Controls 'Mac attachment encoding' setting
---
```
#include <mailmisc.h>
WORD LNPUBLIC MMGetMacAttachEncoding(

	CCHANDLE  hCC);
```
**Description :**

The function  MMGetMacAttachEncoding returns the Conversions Controls 'Mac 
attachment encoding' setting.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  CD to MIME conversion :1 - MultiPart/AppleDouble (default)
				                2 - Application/Mac-BinHex40



**Sample Usage :**
```
WORD wMacAttachEncoding;

wMacAttachEncoding = MMGetMacAttachEncoding(hCC);

```
**See Also :**
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
[MMSetMacAttachEncoding](/domino-c-api-docs/reference/Func/MMSetMacAttachEncoding)
---
