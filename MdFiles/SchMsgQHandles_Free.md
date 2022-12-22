




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



**SchMsgQHandles\_Free** **- Close the
schedule gateway message queues.**


**----------------------------------------------------------------------------------------------------------**



**#include <schgtw.h>**



void
LNPUBLIC **SchMsgQHandles\_Free(**  

      MQHANDLE  hInputQ,  

      MQHANDLE  hOutputQ**);**



**Description :**



This routine
closes the schedule gateway message queues.


 


**Parameters :**



Input :  

hInputQ  -  Handle to an open input queue  

  

hOutputQ  -  Handle to an open output queue  

  




 


 **See Also :**


**[SchMsgQHandles\_New](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/2D785390087BA1E28525635D00822300)**



----------------------------------------------------------------------------------------------------------


 





