




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




**Initial Release 4.0**



**Function : Agents**



**AgentRun** **- Run an
Agent.**


**----------------------------------------------------------------------------------------------------------**



**#include <agents.h>**



STATUS
LNPUBLIC **AgentRun(**  

      HAGENT  hAgent,  

      HAGENTCTX  hAgentCtx,  

      DHANDLE  hSelection,  

      DWORD  dwFlags**);**



**Description :**



Given a
handle to an open Agent (created by calling AgentOpen()) and a handle to an
Agent runtime context (created by calling AgentCreateRunContext()), run the
agent.


 


If the agent
is not a LotusScript agent and it requires input from the UI, (for example the
agent is to run on seclected documents), you will get the error,
ERR\_AGENT\_UI\_TRIGGER:  "Unsupported trigger and search in the background
or embedded agent"


 


If a background
agent erroneously refers to the UI (front-end) classes, you will get an error.


 


**Parameters :**



Input :  

hAgent  -  Handle to the open Agent.  

  

hAgentCtx  -  Handle to the Agent run-time context.  

  

hSelection  -  Reseved;  must be 0.  

  

dwFlags  -  Optional - can be 0.  See AGENT\_xxx for other possible values.  

  




Output :  

(routine)  -  Return indicates either success or what the error is. The return
codes include:   

  

NOERROR - Operation was successful.  

  

ERR\_xxx - STATUS returned from a lower-level unction call.  

  

  




 **Sample Usage :**



/\* Given
the handle of the database and the Agent name, find the Note ID for the
Agent.\*/  

        status = NIFFindDesignNote (hDb, pAgentName, NOTE\_CLASS\_FILTER,
&AgentID);  

        if (status == ERR\_NOT\_FOUND)  

               status = NIFFindPrivateDesignNote (hDb, pAgentName,
NOTE\_CLASS\_FILTER, &AgentID);  

          

/\* Open the Agent \*/   


        status
= AgentOpen (hDb, AgentId, &hOpenAgent);  

  




/\* Create
the Agent Run Context \*/


        status
= AgentCreateRunContext (hOpenAgent, NULL, (DWORD) 0, &hOpenAgentCtx);


 


/\* Run the
Agent \*/


        status
= AgentRun (hOpenAgent, hOpenAgentCtx, (DHANDLE) 0, (DWORD) 0);


 


/\* Destroy
the Agent Run Context \*/


        AgentDestroyRunContext
(hOpenAgentCtx);  

  




/\* Close
the Agent \*/


        AgentClose
(hOpenAgent);


 


 **See Also :**


**[AgentCreateRunContext](AgentCreateRunContext.md)**


**[AgentOpen](AgentOpen.md)**


**[HAGENT](HAGENT.md)**


**[HAGENTCTX](HAGENTCTX.md)**



----------------------------------------------------------------------------------------------------------


 





