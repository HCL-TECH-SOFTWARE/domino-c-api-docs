##### Function : MIME
##### MMCreateConvControls - create a Conversion Controls context.
---
```
#include <mailmisc.h>
STATUS LNPUBLIC MMCreateConvControls(

	CCHANDLE *phCC);
```
**Description :**

The function  MMCreateConvControls creates a Conversions Controls context for 
the reading and writing of various conversion configuration settings.  The 
various settings are initialized to their default settings (the same as those 
set by MMConvDefaults; see below).

**Parameters :**

Output :
(routine)  -  Successfully converted the note.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



phCC  -  pointer to a CCHANDLE.  The handle to the created Conversion Controls context is written here.


**Sample Usage :**
```
STATUS err;
CCHANDLE hCC;

if (err = MMCreateConvControls(&hCC)) {
	goto exit;
}

```
**See Also :**
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
[MMDestroyConvControls](/domino-c-api-docs/reference/Func/MMDestroyConvControls)
[MMConvDefaults](/domino-c-api-docs/reference/Func/MMConvDefaults)
---
