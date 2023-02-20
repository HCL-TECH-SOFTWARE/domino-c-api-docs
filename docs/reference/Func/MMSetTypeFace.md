##### Function : MIME
##### MMSetTypeFace - set Conversion Controls 'typeface' setting.
---
```
#include <mailmisc.h>
void LNPUBLIC MMSetTypeFace(

	CCHANDLE  hCC,
	WORD  wTypeFace);
```
**Description :**

The function  MMSetTypeFace sets the Conversions Controls 'typeface' setting to 
the input value, wTypeFace.  No checking is done for out of bounds values.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

wTypeFace  -  the value to use for the Conversion Controls 'typeface' setting.

Output :
(routine)  -  void



**Sample Usage :**
```
MMSetTypeFace(hCC, 0); /* 0 - Times Roman */
	  /* 1 - Helvetica */
	  /* 2 - Courier (default) */

```
**See Also :**
[CCHANDLE](/reference/Data/CCHANDLE)
[MMGetTypeFace](/reference/Func/MMGetTypeFace)
---
