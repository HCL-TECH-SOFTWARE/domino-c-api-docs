##### Function : Domino Upgrade Services
##### DUSAdvancedDlg - Description of dialog displayed when the "Advanced" button is pushed.
---
##### #include <dus.h>
STATUS LNCALLBACK **DUSAdvancedDlg(**

	DHANDLE  hContext);
**Description :**
When the "Advanced" button is pressed from the People and Groups migration 
dialog, DUSAdvancedDlg() will be called.  Information from the dialog can be 
stored in the buffer represented by hContext.
**Parameters :**
Input :
hContext  -  handle to this DUS' specific context information.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


**See Also :**
[DUSStart](D:/md_files/DUSStart.md)
[fDUSxxx](D:/md_files/fDUSxxx.md)
---
