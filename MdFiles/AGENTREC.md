




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




**Initial Release 4.1**



**Data Type : Billing**



**AGENTREC** **-** Agent
Billing Record


**----------------------------------------------------------------------------------------------------------**



**#include
<billing.h>**



**Definition :**




        typedef
struct                        /\*  Agent Billing Record \*/  

        {  

           WORD        ULen;                  /\*  UserName Len \*/  

           WORD        TLen;                  /\*  TaskName Len \*/  

           WORD        DLen;                  /\*  DatabaseName Len \*/  

           DWORD               ElapsedRunTime;        /\*  Elapsed run-time for
agent \*/  

           DWORD               Flags;         /\*  Agent Flags \*/  

        /\* UserName, TaskName, Database Name strings follow \*/  

        } AGENTREC;


 


 


**Description :**



To create
AGENT billing records you must include the Agent keyword in the notes.ini
BillingClass variable on the billing server.  This enables the server to write
agent-related information to the billing message queue which can then be read
to the AGENTREC structure by the billing server task.


 


For more
information about billing for Domino agents, see the *Domino 5 Administration
Help* documentation.


 


**Structure
Description**



**ULen** -- User
name length


 


**TLen** -- Task name
length


 


**DLen** -- Database
name length


 


**ElapsedRunTime** -- Elapsed
runtime for the agent


 


**Flags** -- Agent
flags


 **See Also :**


**[BILLMSG](BILLMSG.md)**


**[BILLREC](BILLREC.md)**


**[BILL\_xxx (actions)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6A3C76AFC8056835852563010073FD5F)**


**[DBREC](DBREC.md)**


**[DOCUMENT](DOCUMENT.md)**


**[HTTPREQREC](HTTPREQREC.md)**


**[MAILREC](MAILREC.md)**


**[REPLREC](REPLREC.md)**



----------------------------------------------------------------------------------------------------------


 





