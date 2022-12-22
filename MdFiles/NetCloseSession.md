




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




 


**Function : Network Send and Receive**



**NetCloseSession** **- Closes a
network session.**


**----------------------------------------------------------------------------------------------------------**



**#include <net.h>**



void
LNPUBLIC **NetCloseSession(**  

      SESSIONID  SessionID**);**



**Description :**



This
function closes a network session.  If a phone call had been made (by NetLink)
in order to create that session, the phone call is hung up by NetCloseSession.


 


**Parameters :**



Input :  

SessionID  -  A Session ID obtained in a previous call to NetLink.  

  




Output :  

(routine)  -  None  

  

  




 **See Also :**


**[NetLink](NetLink.md)**



----------------------------------------------------------------------------------------------------------


 





