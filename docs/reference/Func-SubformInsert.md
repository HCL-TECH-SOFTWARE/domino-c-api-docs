##### Function : Form
##### SubformInsert - Insert subform into form or subform design note.
---
##### #include <easycd.h>
STATUS LNPUBLIC **SubformInsert(**

	DBHANDLE  hDB,
	char *pSubForm,
	char *pForm,
	DWORD  Flags);
**Description :**
This function appends a subform to another form or subform.  Please see Chapter 
8-1 Forms in the User Guide for information on how to create a subform.
**Parameters :**
Input :
hDB  -  Handle to the database.

pSubForm  -  Subform name to attach.

pForm  -  Parent form name or subform name that will contain the inserted subform.

Flags  -  Subforms are implemented as a hotspot.  You may specify some of the hotspot attributes with this parameter.  This would be equivalent to setting the Flags member of a CDHOTSPOTBEGIN record.   See HOTSPOTREC_RUNFLAG_xxx  for possible values.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR
ERR_xxx - Errors returned by lower level Notes functions.  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user.


**See Also :**
[SubformRemove](D:/md_files/SubformRemove.md)
[HOTSPOTREC_RUNFLAG_xxx](D:/md_files/HOTSPOTREC_RUNFLAG_xxx.md)
---
