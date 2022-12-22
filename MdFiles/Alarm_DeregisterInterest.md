




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



**Function : Alarms**



**Alarm\_DeregisterInterest** **-
Deregister interest in alarms.**


**----------------------------------------------------------------------------------------------------------**



**#include <alarm.h>**



STATUS
LNPUBLIC **Alarm\_DeregisterInterest(**  

      char far \*pszClientName,  

      WORD  Flags**);**



**Description :**



Called by
the client when it is terminating.  The alarms process will remove this client
from its list.  If the list is empty the Alarms daemon will also terminate.


 


**Parameters :**



Input :  

pszClientName  -  The client name.  

  

Flags  -  Unused, pass in 0.  

  




Output :  

(routine)  -  NOERROR - Successfully deregistered interest in alarms.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

  




 **See Also :**


**[Alarm\_RegisterInterest](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/DA1692F20B55D10D852563DC0060803E)**



----------------------------------------------------------------------------------------------------------


 





