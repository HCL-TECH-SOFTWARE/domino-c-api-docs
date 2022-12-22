




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




**Initial Release 6**



**Function : Extension Manager; Mail;
SMTP**



**SMTPConnectEMCallback** **- Extension
Manager callback for EM\_SMTPCONNECT**


**----------------------------------------------------------------------------------------------------------**



**Note:** This function is only available as an Extension Manager callback
-- you cannot call this function directly.


 


**#include <extmgr.h>**



STATUS
LNPUBLIC **SMTPConnectEMCallback(**  

      DWORD  SessionID,  

      char \*RemoteIP,  

      char \*RemoteHost,  

      BOOL &  PossibleRelay,  

      char \*Greeting,  

      DWORD  MaxGreetingLength**);**



**Description :**



EM\_SMTPCONNECT
is called when an inbound SMTP connection has been detected.


      


The
Extension Manager EM\_BEFORE notification type for the EM\_SMTPCONNECT event
occurs when an inbound SMTP connection has been detected and prior to the
execution of the internal Domino SMTP restriction controls.  The callback
routine can implement its own anti-relay checks and/or bypass Domino related
checks through the use of PossibleRelay BOOL and return status of value
NOERROR.  Return STATUS other than ERR\_EM\_CONTINUE or NOERROR sets AccessDenied
flag which causes subsequent commands to be rejected.  


 


The
Extension Manager EM\_AFTER notification type for the EM\_SMTPCONNECT event
occurs after the SMTP listener task has accepted the connection but prior to
sending the SMTP greeting to the connecting host.


 


**Parameters :**



Input :  

SessionID  -  Unique session identifier for the current process.  

  

RemoteIP  -  NULL terminated string containing IP address of connecting host.  

  

RemoteHost  -  NULL terminated string containing host name of connecting host
if reverse DNS lookup was successful.  If lookup was unsuccessful, the string
length will be zero.   

  

PossibleRelay  -  Indicator whether connecting host should be treated as
possible relay or not.  

  

MaxGreetingLength  -  Size of buffer allocated to modify Greeting.  

  




Output :  

(routine)  -  Return status from the call   

EM\_BEFORE event: NOERROR indicates to skip configured relay and RBL checks;
Value other than  ERR\_EM\_CONTINUE indicates further commands should be rejected
from host.  

EM\_AFTER event: Value other than ERR\_EM\_CONTINUE is ignored.  

  

  

Greeting  -  EM\_BEFORE event: NULL; EM\_AFTER event: Greeting that will be
returned to the connecting host.  Callback routine can modify the string.  

  




 **See Also :**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**



----------------------------------------------------------------------------------------------------------


 





