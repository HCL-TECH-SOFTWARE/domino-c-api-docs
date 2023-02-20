##### Function : MIME
##### MMDestroyConvControls - destroy a Conversion Controls context.
---
```
#include <mailmisc.h>
STATUS LNPUBLIC MMDestroyConvControls(

	CCHANDLE  hCC);
```
**Description :**

The function MMDestroyConvControls destroys a Conversions Controls context, 
freeing memory previously allocated for the conversion configuration settings.


**Parameters :**
Input :
hCC  -  a CCHANDLE to a Conversion Controls context created by a previous call to MMCreateConvControls.

Output :
(routine)  -  Successfully converted the note.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.




**Sample Usage :**
```
STATUS err;

if (err = MMDestroyConvControls(hCC)) {
	goto exit;
}

```
**See Also :**
[CCHANDLE](/reference/Data/CCHANDLE)
[MMCreateConvControls](/reference/Func/MMCreateConvControls)
---
