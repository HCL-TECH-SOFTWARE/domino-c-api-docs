##### Function : MIME
##### MMConvDefaults - set a Conversion Controls configuration settings to their default values.
---
```
#include <mailmisc.h>
void LNPUBLIC MMConvDefaults(

	CCHANDLE  hCC);
```
**Description :**

The function MMConvDefaults set Conversion Controls configuration settings to 
their default values.

**Parameters :**
Input :
hCC  -   a CCHANDLE to a Conversion Controls context created by a previous call to MMCreateConvControls.

Output :
(routine)  -  void



**Sample Usage :**
```
MMConvDefaults(hCC);
```
**See Also :**
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
[MMCreateConvControls](/domino-c-api-docs/reference/Func/MMCreateConvControls)
---
