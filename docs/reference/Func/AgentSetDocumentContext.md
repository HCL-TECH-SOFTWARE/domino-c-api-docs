##### Function : Agents
##### AgentSetDocumentContext - Assigns open document to current agent runtime context handle.
---
```
#include <agents.h>
STATUS LNPUBLIC AgentSetDocumentContext(

	HAGENTCTX  hAgentCtx,
	NOTEHANDLE  hNote);
```
**Description :**

This routine provides a mechanism to pass a "parameter" note to a LotusScript 
agent action by assigning an open document note handle to the current agent 
runtime context handle, as created by a previous call to 
AgentCreateRunContext().  The document associated with the open note handle 
that is passed to this routine would typically consist of a one to many items 
that contain values corresponding to input parameters the agent action 
script.   A subsequent call to AgentRun() will pass the note handle to 
LotusScript via a special property of the back-end NotesSession class.   This 
class is defined as follows.   

	NotesDocument = NotesSession.DocumentContext

The NotesDocument can be instantiated by the action script routine, and its 
field values can be read in as parameters to the LotusScript subroutine.   
Since the document context is assigned to the current runtime context handle, 
it should be reset before each call to AgentRun().

**Parameters :**
Input :
hAgentCtx  -  Handle to the Agent runtime context.

hNote  -  Handle to the open "parameter" document.

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include: 

NOERROR - Operation was successful.

ERR_xxx - STATUS returned from a lower-level function call.




**See Also :**
[AgentCreateRunContext](/domino-c-api-docs/reference/Func/AgentCreateRunContext)
[HAGENTCTX](/domino-c-api-docs/reference/Data/HAGENTCTX)
---
