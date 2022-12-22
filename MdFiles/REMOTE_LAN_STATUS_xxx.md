




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



**Symbolic Value : Remote LAN adapter**



**REMOTE\_LAN\_STATUS\_xxx** **-** Status codes
that a remote LAN adapter can pass to a Notes status callback routine.


**----------------------------------------------------------------------------------------------------------**



**#include <net.h>**


 **Symbolic Values :**      REMOTE\_LAN\_STATUS\_STARTING\_CONNECTION           -  Calling
remote LAN.  

  

      REMOTE\_LAN\_STATUS\_PHYSICALLY\_CONNECTED         -  Connected to remote
LAN.  

  

      REMOTE\_LAN\_STATUS\_AUTHENTICATING           -  Authenticating with remote
LAN.  

  

      REMOTE\_LAN\_STATUS\_AUTHENTICATED            -  Authenticated.  

  

      REMOTE\_LAN\_STATUS\_WAITING\_FOR\_CALLBACK          -  Waiting for call back.  

  

      REMOTE\_LAN\_STATUS\_LINK\_ESTABLISHED        -  Remote LAN link established.  

  

      REMOTE\_LAN\_STATUS\_LINK\_FAILED        -  Link to remote LAN failed.  

  

      REMOTE\_LAN\_STATUS\_HANGING\_UP      -  Terminating remote LAN link.  

  

      REMOTE\_LAN\_STATUS\_HANGUP\_COMPLETE      -  Remote LAN link terminated.  

  




**Description :**



These status
codes are used by a remote LAN adapter in calls to the Notes remote LAN adapter
status callback routine when the Action parameter is specified as
REMOTE\_LAN\_DISPLAY\_STATUS.  The remote LAN adapter specifies one of these
status codes to the Notes remote LAN adapter callback routine in order for
Notes to display the status information. 


 **See Also :**


**[PREMOTE\_LAN\_STATUS\_CALLBACK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/AF43F4D888713FA785256361003C0CB5)**



----------------------------------------------------------------------------------------------------------


 





