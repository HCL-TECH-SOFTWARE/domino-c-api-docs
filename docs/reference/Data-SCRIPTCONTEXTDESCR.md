##### Data Type : Agents
##### SCRIPTCONTEXTDESCR - Structure for passing LotusScript context information.
---
##### #include <agents.h>
**Description :**
This structure is used to pass the LotusScript context information to the 
AgentLSTextFormat API.  Following are the name of the context class assigned 
for each LotusScript context:

If the LotusScript was contained in: 	Specify the following text as 
"szNameOfContextClass":
Form	NOTESUIDOCUMENT
Page	NOTESUIDOCUMENT
Subform	NOTESUIDOCUMENT
View	NOTESUIVIEW
Action	BUTTON
Field	FIELD
Database Script	NOTESUIDATABASE


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
[AgentLSTextFormat](D:/md_files/AgentLSTextFormat.md)
---
