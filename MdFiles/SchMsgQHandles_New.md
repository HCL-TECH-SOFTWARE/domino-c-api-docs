




<!--
 /\* Font Definitions \*/
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




**Initial Release 4.5**



**Function : Calendaring and
Scheduling**



**SchMsgQHandles\_New** **- Prepare
message queues.**


**----------------------------------------------------------------------------------------------------------**



**#include <schgtw.h>**



STATUS
LNPUBLIC **SchMsgQHandles\_New(**  

      char FAR \*szServerName,  

      BOOL  fCreate,  

      MQHANDLE FAR \*rethInputQ,  

      MQHANDLE FAR \*rethOutputQ**);**



**Description :**



This
prepares the message queues that we send/receive messages on.


 


**Parameters :**



Input :  

szServerName  -  Points to the server name, if it is NULL then this is a native
Domino request, else this is the name of the gateway.  

  

fCreate  -  Set this to TRUE if the queues should be created if they don't
already exist. Note: only the "gateway" should create the queues.
Alls gateway clients should pass this parameter as FALSE.  

  




Output :  

(routine)  -  NOERROR - Successfully prepared the message queue.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

rethInputQ  -  Points to where we return the handle to the input queue  

  

rethOutputQ  -  Points to where we return the handle to the output queue.  

  




 **See Also :**


**[SchMsgQHandles\_Free](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F8D5D9D5C8F926CC8525635D008297C2)**



----------------------------------------------------------------------------------------------------------


 





