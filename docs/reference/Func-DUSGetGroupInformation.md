##### Function : Domino Upgrade Services
##### DUSGetGroupInformation - Get group information for display.
---
##### #include <dus.h>
STATUS LNCALLBACK **DUSGetGroupInformation(**

	DHANDLE  hContext,
	char *GroupName,
	NOTEHANDLE  hGroupNote);
**Description :**
Returns full information about the group for display immediately after the 
administrator has selected the group from the available list.
**Parameters :**
Input :
hContext  -  Handle to this DUS' specific context information.

GroupName  -  Name of the group selected (originally supplied by the DUS with DUSRetrieveGroups)

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


hGroupNote  -  A handle to the group note.

**See Also :**
[DUSGetUserInformation](D:/md_files/DUSGetUserInformation.md)
---
