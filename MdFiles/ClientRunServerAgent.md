




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Server**



**ClientRunServerAgent** **- Execute
an agent on the server.**


**----------------------------------------------------------------------------------------------------------**



**#include <client.h>**



STATUS
 **ClientRunServerAgent(**  

      DBHANDLE  hDB,  

      NOTEID  anid,  

      NOTEID  nidParamDoc,  

      BOOL  bForeignServer,  

      BOOL  bSuppressPrintToConsole**);**



**Description :**



If the
caller has privileges to do so, execute an agent on the server.


 


**Parameters :**



Input :  

hDB  -  Database handle where agent lives.  

  

anid  -  Noteid of the agent to run.  

  

nidParamDoc  -  Noteid of ParamDoc.  

  

bForeignServer  -  If the caller is a server calling another Server.  

  

bSuppressPrintToConsole  -  Turn off (or not) the agent's ability to write to
the server console.  

  




Output :  

(routine)  -  Returns STATUS from code.  

  

  




 **Sample Usage :**


      // Run
it, wait for it to complete. 


            STATUS
error = NOERROR; 


                        error
= ClientRunServerAgent(hDb, noteid, nidParamDoc, bForeignServer,
bSuppressPrintToConsole);


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





