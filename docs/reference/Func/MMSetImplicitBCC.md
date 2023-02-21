##### Function : MIME
##### MMSetImplicitBCC - set Conversion Controls 'implicit BCC' setting
---
```
#include <mailmisc.h>
void LNPUBLIC MMSetImplicitBCC(

	CCHANDLE  hCC,
	BOOL  bImplicitBCC);
```
**Description :**

The function  MMSetImplicitBCC sets the Conversions Controls 'implicit BCC' 
setting to the input value, bImplicitBCC.  No checking is done for out of 
bounds values.


**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

bImplicitBCC  -  the value to use for the Conversion Controls 'implicit BCC' setting.

Output :
(routine)  -  void



**Sample Usage :**
```
MMSetImplicitBCC(hCC, FALSE); /* if TRUE, add a BCC for every recipient not 
listed in a To, CC, or Bcc header (default FALSE) */
```
**See Also :**
[MMGetImplicitBCC](/domino-c-api-docs/reference/Func/MMGetImplicitBCC)
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
---
