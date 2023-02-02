##### Function : Domino Upgrade Services
##### DUSStop - Notifies the DUS that this is the end of this DUS session.
---
##### #include <dus.h>
STATUS LNCALLBACK **DUSStop(**

	DHANDLE  hContext);
**Description :**
This function notifies the DUS that the end of this session is over.  Memory 
associated with the context handle, allocated in DUSStart(), should now be 
freed.  
**Parameters :**
Input :
hContext  -  handle to this DUS' specific context information.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


**See Also :**
[](D:/md_files/.md)
---
