##### Function : Domino Upgrade Services
##### DUSStart - Initializes the DUS (Domino Upgrade Services) environment.
---
##### #include <dus.h>
STATUS LNCALLBACK **DUSStart(**

	HMODULE  hInstance,
	DHANDLE *pRethContext,
	NOTEHANDLE  hUserNote,
	DWORD *pRetInitFlags,
	DUSPROGRESSBARPROC  DUSProgressBar,
	DUSLOGEVENTPROC  DUSLogEvent);
**Description :**
This function notifies the DUS of one of two situations:
	1) It has been selected from the Foreign Directory Import source list 
in the Foreign Directory Import dialog.
	2) The first of possibly several users retrieved from this DUS is about 
to be registered with Domino Administration.
It also supplies the DUS framework with a context handle, which will be passed 
back to the DUS with every subsequent DUS.... function call.  
**Parameters :**
Input :
hInstance  -  Instance handle to the DUS DLL.

hUserNote  -  this note handle will only be valid  (non-NULL) if DUSStart() is called just prior to user registration.  When DUSStart() is called from the Foreign Directory dialog, hUserNote will be NULLHANDLE and the DUS allocates and initializes a context buffer for the first time.

pRetInitFlags  -  DUS Initialization flags.  Refer to fDUSxxx.

DUSProgressBar  -  pointer to a callback function used by the DUS to display progress on potentially lengthy operations, such as user retrieval.

DUSLogEvent  -  pointer to a callback function used by the DUS to log progress to the Domino log on any operation, such as user retrieval.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


pRethContext  -  pointer to a context handle the DUS can optionally allocate/return to the DUS framework.  On every subsequent call to the DUS in the current session, this context handle will be passed to the DUS by the DUS framework.  The DUS is responsible for freeing this handle in DUSStop().  Can be NULL.

**See Also :**
[DUSLOGEVENTPROC](D:/md_files/DUSLOGEVENTPROC.md)
[DUSPROGRESSBARPROC](D:/md_files/DUSPROGRESSBARPROC.md)
[fDUSxxx](D:/md_files/fDUSxxx.md)
---
