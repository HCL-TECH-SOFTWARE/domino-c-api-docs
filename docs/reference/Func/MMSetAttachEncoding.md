##### Function : MIME
##### MMSetAttachEncoding - set Conversion Controls 'attachment encoding' setting
---
```
#include <mailmisc.h>
void LNPUBLIC MMSetAttachEncoding(

	CCHANDLE  hCC,
	WORD  wAttachEncoding);
```
**Description :**

The function  MMSetAttachEncoding sets the Conversions Controls 'attachment 
encoding' setting to the input value, wAttachEncoding.  No checking is done for 
out of bounds values.


**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

wAttachEncoding  -  the value to use for the Conversion Controls 'attachment encoding' setting.

Output :
(routine)  -  void



**Sample Usage :**
```
MMSetAttachEncoding(hCC, 0); /* 1 - base64 (default) */
	    /* 2 - quoted-printable */
	    /* 3 - uuencode */
	    /* 4 - binhex 4.0 */

```
**See Also :**
[MMGetAttachEncoding](/reference/Func/MMGetAttachEncoding)
[CCHANDLE](/reference/Data/CCHANDLE)
---
