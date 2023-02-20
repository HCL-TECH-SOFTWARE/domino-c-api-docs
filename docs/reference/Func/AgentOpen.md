##### Function : Agents
##### AgentOpen - Open a note containing an Agent.
---
```
#include <agents.h>
STATUS LNPUBLIC AgentOpen(

	DHANDLE  hDB,
	NOTEID  AgentNoteID,
	HAGENT far *rethAgent);
```
**Description :**

Open the note (identified by note ID) containing an Agent.  The handle returned 
by this function must be closed by calling AgentClose().

**Parameters :**
Input :
hDB  -  Handle to an open Domino database.

AgentNoteID  -  ID of the note containing the Agent.

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include: 

NOERROR - Operation was successful.

ERR_xxx - STATUS returned from a lower-level function call.


rethAgent  -  Handle to the open agent.


**See Also :**
[AgentClose](/reference/Func/AgentClose)
[AgentCreateRunContext](/reference/Func/AgentCreateRunContext)
[AgentRun](/reference/Func/AgentRun)
[HAGENT](/reference/Data/HAGENT)
---
