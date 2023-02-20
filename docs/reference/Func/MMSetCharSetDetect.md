##### Function : MIME
##### MMSetCharSetDetect - set Conversion Controls 'character set detect' setting
---
```
#include <mailmisc.h>
void LNPUBLIC MMSetCharSetDetect(

	CCHANDLE  hCC,
	BOOL  bCharSetDetect);
```
**Description :**

The function  MMSetCharSetDetect sets the Conversions Controls 'character set 
detect' setting to the input value, bCharSetDetect.  No checking is done for 
out of bounds values.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

bCharSetDetect  -  the value to use for the Conversion Controls 'character set detect' setting.

Output :
(routine)  -  void



**Sample Usage :**
```
MMSetCharSetDetect(hCC, TRUE); /* if TRUE auto-detect if necessary when 
converting MIME to CD (default is FALSE) */
```
**See Also :**
[MMGetCharSetDetect](/reference/Func/MMGetCharSetDetect)
[CCHANDLE](/reference/Data/CCHANDLE)
---
