##### Function : Domino Upgrade Services
##### DUSGetName - Provide UI string immediately after the DUS dll is loaded.
---
##### #include <dus.h>
STATUS LNCALLBACK **DUSGetName(**

	HMODULE  hInstance,
	char *DUSNameBuf,
	WORD  DUSNameBufLen,
	char *DUSDescriptionBuf,
	WORD  DUSDescriptionBufLen);
**Description :**
This call notifies the upgrade DLL that the upgrade dialog is being displayed.  
It also passes in the instance handle of the DUS, which the DUS may want to 
store for later DUS operations.
**Parameters :**
Input :
hInstance  -  instance handle of this DUS.

DUSNameBufLen  -  size of the DUSNameBuf.

DUSDescriptionBufLen  -  size of the DUSDescriptionbuf.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


DUSNameBuf  -  buffer into which the DUS will copy the name of the DUS as it will appear in the Foreign Directory Source listbox (in the upgrade dialog).

DUSDescriptionBuf  -  buffer into which the DUS will copy a brief description of the DUS as it will appear in the upgrade dialog.

**See Also :**
[](D:/md_files/.md)
---
