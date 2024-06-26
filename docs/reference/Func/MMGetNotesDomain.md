##### Function : MIME
##### MMGetNotesDomain - get Conversion Controls 'Notes domain' setting
---
```
#include <mailmisc.h>
char * LNPUBLIC MMGetNotesDomain(

	CCHANDLE  hCC);
```
**Description :**

The function  MMGetNotesDomain returns the Conversions Controls 'Notes domain' 
setting.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  Local notes domain, used to construct 821 addresses (default is NULL)



**Sample Usage :**
```
char * pszNotesDomain;

pszNotesDomain = MMGetNotesDomain(hCC);

```
**See Also :**
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
[MMSetNotesDomain](/domino-c-api-docs/reference/Func/MMSetNotesDomain)
---
