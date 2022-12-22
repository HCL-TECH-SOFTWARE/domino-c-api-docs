




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




**Initial Release 4.0**



**Function : Mail Gateway**



**MailUnloadRoutingTables** **- Unload
mail routing tables from memory.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailUnloadRoutingTables(**  

      DHANDLE  hTables**);**



**Description :**



Unload the
routing tables from memory and free the memory allocated.


 


**Parameters :**



Input :  

hTables  -  Handle to the memory block containing the mail routing tables.  

  




Output :  

(routine)  -  Return status from this call -- indicates either sucess or what
the error is.  

  

  




 **See Also :**


**[MailLoadRoutingTables](MailLoadRoutingTables.md)**


**[MailReloadRoutingTables](MailReloadRoutingTables.md)**



----------------------------------------------------------------------------------------------------------


 





