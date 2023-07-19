##### Data Type : Agents
##### SCRIPTCONTEXTDESCR - Structure for passing LotusScript context information.
---
```
#include <agents.h>
```

**Definition :**

typedef struct {
	DWORD Length;
	char  szNameOfContextClass[MAXIMUM_ID_NAME_LENGTH + 1];
}SCRIPTCONTEXTDESCR;

**Description :**

This structure is used to pass the LotusScript context information to the AgentLSTextFormat API.  Following are the name of the context class assigned for each LotusScript context:<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="35%"><b>If the LotusScript was contained in: </b></td><td width="65%"><b>Specify the following text as &quot;szNameOfContextClass&quot;:</b></td></tr>

<tr valign="top"><td width="35%">Form</td><td width="65%">NOTESUIDOCUMENT</td></tr>

<tr valign="top"><td width="35%">Page</td><td width="65%">NOTESUIDOCUMENT</td></tr>

<tr valign="top"><td width="35%">Subform</td><td width="65%">NOTESUIDOCUMENT</td></tr>

<tr valign="top"><td width="35%">View</td><td width="65%">NOTESUIVIEW</td></tr>

<tr valign="top"><td width="35%">Action</td><td width="65%">BUTTON</td></tr>

<tr valign="top"><td width="35%">Field</td><td width="65%">FIELD</td></tr>

<tr valign="top"><td width="35%">Database Script</td><td width="65%">NOTESUIDATABASE</td></tr>
</table>



**Sample Usage :**
```
Here is the code snippet for filling up the SCRIPTCONTEXTDESCR structure if a 
LotusScript was contained in a button:

    
     SCRIPTCONTEXTDESCR * pSCD;
            HANDLE hData = NULLHANDLE;

           error = OSMemAlloc(0,sizeof(SCRIPTCONTEXTDESCR),&hData);
           pSCD = OSLock(SCRIPTCONTEXTDESCR,hData);

           pSCD->Length = sizeof(SCRIPTCONTEXTDESCR);
           strcpy(pSCD->szNameOfContextClass, "BUTTON" );

           OSUnlock( hData);

           AgentLSTextFormat( hSrc, &hDest, &hErrs, dwFlags, &hData ); 
	
```

**See Also :**
[AgentLSTextFormat](/domino-c-api-docs/reference/Func/AgentLSTextFormat)
---
