##### Function : LotusScript
##### NSFNoteLSCompileExt - Extended form of NSFNoteLSCompile
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFNoteLSCompileExt(

	DBHANDLE  hDb,
	NOTEHANDLE  hNote,
	DWORD  dwFlags,
	LSCOMPILEERRPROC  pfnErrProc,
	void*pCtx);
```
**Description :**

This API is an extended form of NSFNoteLSCompile which returns additional error 
information if there are any compilation errors when LotusScript code within 
the note is compiled.

**Parameters :**
Input :
hDb  -  Handle to the note containing LotusScript modules.

hNote  -  Handle to the note containing LotusScript modules.

dwFlags  -  (Reserved for future use) Must be 0.

pfnErrProc  -  pointer to a callback function that is called if there are any compilation errors

pCtx  -  pointer to user-defined data which allows the application to pass contextual data to the callback function.

Output :
(routine)  -  (routine)  -  Return indicates either success or what the error is. The return codes include: 

NOERROR - Operation was successful.

ERR_NULL_NOTEHANDLE -  if hNote was not specified.

ERR_xxx - STATUS returned from a lower level Notes function call.



**See Also :**
[LSCOMPILEERRPROC](/reference/Data/LSCOMPILEERRPROC)
[LSCOMPILE_ERR_INFO;](/reference/Data/LSCOMPILE_ERR_INFO;)
[NSFNoteLSCompile](/reference/Func/NSFNoteLSCompile)
---
