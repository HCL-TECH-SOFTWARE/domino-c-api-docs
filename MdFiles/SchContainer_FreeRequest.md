




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



**SchContainer\_FreeRequest** **- Free a
request**


**----------------------------------------------------------------------------------------------------------**



**#include <schgtw.h>**



STATUS
LNPUBLIC **SchContainer\_FreeRequest(**  

      DHANDLE  hCntnr,  

      HCNTNROBJ  hRqst**);**



**Description :**



This routine
is used to free a request. Requests are used to obtain free time information
from a foreign system calendaring and scheduling gateway.


 


**Parameters :**



Input :  

hCntnr  -  The container handle.  

  

hRqst  -  Pointer to the object to free.  

  




Output :  

(routine)  -  NOERROR - Successfully freed a request.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

  




 **See Also :**


**[SchContainer\_GetRequest](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/133E592859D0BDAD482573FB003235D7)**



----------------------------------------------------------------------------------------------------------


 





