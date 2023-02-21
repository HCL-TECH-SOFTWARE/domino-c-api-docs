##### Function : MIME
##### MMSetStripGroups - set Conversion Controls 'strip groups from addresses' setting
---
```
#include <mailmisc.h>
void LNPUBLIC MMSetStripGroups(

	CCHANDLE  hCC,
	BOOL  bStripGroups);
```
**Description :**

The function  MMSetStripGroups sets the Conversions Controls 'strip groups from 
addresses' setting to the input value, bStripGroups.  No checking is done for 
out of bounds values.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

bStripGroups  -  the value to use for the Conversion Controls 'strip groups from addresses' setting.

Output :
(routine)  -  void



**Sample Usage :**
```
MMSetStripGroups(hCC, TRUE); /* if TRUE strip groups from all addresses when 
importing (default is FALSE) */
```
**See Also :**
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
[MMGetStripGroups](/domino-c-api-docs/reference/Func/MMGetStripGroups)
---
