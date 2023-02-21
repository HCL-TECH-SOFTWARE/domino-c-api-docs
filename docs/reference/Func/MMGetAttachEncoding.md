##### Function : MIME
##### MMGetAttachEncoding - get Conversion Controls 'attachment encoding' setting.
---
```
#include <mailmisc.h>
WORD LNPUBLIC MMGetAttachEncoding(

	CCHANDLE  hCC);
```
**Description :**

The function  MMGetAttachEncoding returns the Conversions Controls 'attachment 
encoding' setting.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  1 - base64 (default)
	           2 - quoted-printable
	           3 - uuencode
	           4 - binhex 4.0



**Sample Usage :**
```
WORD wAttachEncoding;

wAttachEncoding = MMGetAttachEncoding(hCC);

```
**See Also :**
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
[MMSetAttachEncoding](/domino-c-api-docs/reference/Func/MMSetAttachEncoding)
---
