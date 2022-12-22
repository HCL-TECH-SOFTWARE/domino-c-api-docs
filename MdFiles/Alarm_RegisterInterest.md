




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



**Alarm\_RegisterInterest** **- Register
interest in receiving alarms.**


**----------------------------------------------------------------------------------------------------------**



**#include <alarm.h>**



STATUS
LNPUBLIC **Alarm\_RegisterInterest(**  

      char far \*pszClientName,  

      WORD  Flags**);**



**Description :**



Register
this client as having an interest in receiving alarms. Alarms daemon will be
started if none running.


 


**Parameters :**



Input :  

pszClientName  -  Standard name of the client which will be used by the alarms
daemon to determine if this is a preferred client for displaying alarms.  

  

Flags  -  Not used, pass in 0.  

  




Output :  

(routine)  -  NOERROR - Successfully registered interest in receiving alarms.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

  




 **See Also :**


**[Alarm\_DeregisterInterest](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/715C29C6E0EE6C3F852563DC00616883)**



----------------------------------------------------------------------------------------------------------


 





