##### Function : Domino Upgrade Services
##### DUSGetGroupMembers - Returns membership information about the group.
---
##### #include <dus.h>
STATUS LNCALLBACK **DUSGetGroupMembers(**

	DHANDLE  hContext,
	char *GroupName,
	NOTEHANDLE  hGroupNote,
	DHANDLE *phGroupMembersList,
	DHANDLE *phUserMembersList);
**Description :**
Retrieves all members within the group.  These members may or may not be 
selected by the administrator within the group dialog.
**Parameters :**
Input :
hContext  -  handle to this DUS' specific context information.

GroupName  -  name of the group selected.

Output :
(routine)  -  Return status from the call -- indicates either success (NOERROR) or what the error is.


hGroupNote  -  a handle to the group note.

phGroupMembersList  -  allocated by the DUS, this is a list containing all of the immediate group members of the Group identified by GroupName.

phUserMembersList  -  allocated by the DUS, this is a list containing all of the user members of the Group identified by GroupName.

**See Also :**
[](D:/md_files/.md)
---
