##### Function : Agents
##### SetParamNoteID - Set the NoteID.
---
```
#include <agents.h>
STATUS SetParamNoteID(

	HAGENTCTX  hAgentCtx,
	NOTEID  nid);
```
**Description :**

Passes a NoteID as an argument to the Agent class RunOnServer method. Sets the 
ID on the server side of a Notes Remote Procedure Call (NRPC) transaction so 
that the server agent can access it as a property of the Agent class.

**Parameters :**
Input :
hAgentCtx  -  The agent context.

nid  -  The note ID.

Output :
(routine)  -  Returns status from the call, either success or an error.



**Sample Usage :**
```
	/* Presumes HAGENTCTX hagentctx and NOTEID NoteID. */ 

	SetParamNoteID(hAgentCtx, NoteID); 
```
**See Also :**
---
