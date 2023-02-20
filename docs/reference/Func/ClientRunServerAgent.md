##### Function : Server
##### ClientRunServerAgent - Execute an agent on the server.
---
```
#include <client.h>
STATUS  ClientRunServerAgent(

	DBHANDLE  hDB,
	NOTEID  anid,
	NOTEID  nidParamDoc,
	BOOL  bForeignServer,
	BOOL  bSuppressPrintToConsole);
```
**Description :**

If the caller has privileges to do so, execute an agent on the server.

**Parameters :**
Input :
hDB  -  Database handle where agent lives.

anid  -  Noteid of the agent to run.

nidParamDoc  -  Noteid of ParamDoc.

bForeignServer  -  If the caller is a server calling another Server.

bSuppressPrintToConsole  -  Turn off (or not) the agent's ability to write to the server console.

Output :
(routine)  -  Returns STATUS from code.



**Sample Usage :**
```
	// Run it, wait for it to complete. 
	STATUS error = NOERROR; 
	 error = ClientRunServerAgent(hDb, noteid, nidParamDoc, bForeignServer, 
bSuppressPrintToConsole);
```
**See Also :**
---
