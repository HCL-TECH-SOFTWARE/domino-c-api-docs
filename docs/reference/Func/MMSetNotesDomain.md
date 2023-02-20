##### Function : MIME
##### MMSetNotesDomain - set Conversion Controls 'Notes domain' setting
---
```
#include <mailmisc.h>
void LNPUBLIC MMSetNotesDomain(

	CCHANDLE  hCC,
	char *pszNotesDomain);
```
**Description :**

The function  MMSetNotesDomain sets the Conversions Controls 'Notes domain' 
setting to the input value, pszNotesDomain.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

pszNotesDomain  -  the value to use for the Conversion Controls 'Notes domain' setting.

Output :
(routine)  -  void



**Sample Usage :**
```
char *pszNotesDomain = "Flippant";

MMSetNotesDomain(hCC, pszNotesDomain); /* Local notes domain, used to construct 
821 addresses (default is NULL) */

```
**See Also :**
[CCHANDLE](/reference/Data/CCHANDLE)
[MMGetNotesDomain](/reference/Func/MMGetNotesDomain)
---
