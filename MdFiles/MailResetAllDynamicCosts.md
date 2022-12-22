




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



**MailResetAllDynamicCosts** **- Reset all
dynamic costs.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



BOOL
LNPUBLIC **MailResetAllDynamicCosts(**  

      DHANDLE  hTables**);**



**Description :**



The mail
routing tables contain an estimate of the "cost" to reach a given
server (the amount of effort needed to transfer mail to that server).  There is
also a "dynamic cost" value which mail gateway applications can use
for minor adjustments to this cost value.  The dynamic cost may be -1, 0, or
+1, and is added to the cost value for each hop when determining the best route
to a given server.


 


This
function resets all the dynamic cost values to 0.


 


**Parameters :**



Input :  

hTables  -  Handle to the memory block containing the mail routing tables.  

  




Output :  

(routine)  -  TRUE if any of the dynamic cost values were non-zero, FALSE if
all were zero.  

  

  




 **See Also :**


**[MailLoadRoutingTables](MailLoadRoutingTables.md)**


**[MailReloadRoutingTables](MailReloadRoutingTables.md)**


**[MailSetDynamicCost](MailSetDynamicCost.md)**


**[MailUnloadRoutingTables](MailUnloadRoutingTables.md)**



----------------------------------------------------------------------------------------------------------


 





