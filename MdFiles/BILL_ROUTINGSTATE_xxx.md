




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




**Initial Release 5.0**



**Symbolic Value : Billing**



**BILL\_ROUTINGSTATE\_xxx** **-** MAILREC -
RoutingState


**----------------------------------------------------------------------------------------------------------**



**#include <billing.h>**


 **Symbolic Values :**      BILL\_ROUTINGSTATE\_PENDING    -  Message is pending delivery.  

  

      BILL\_ROUTINGSTATE\_DEAD          -  Message is dead. ("DEAD")  

  

      BILL\_ROUTINGSTATE\_HOLD          -  Message is being held after
non-delivery. ("HOLD")  

  




**Description :**



The router
adds an item (see MAIL\_ROUTINGSTATE\_ITEM\_NUM) to non-deliverable messages.  The
value of this item follows the description of each (non-delivery) symbol above.


 **See Also :**


**[MAILREC](MAILREC.md)**


**[MAIL\_xxx\_ITEM\_NUM(1)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255CF1005E1A42)**



----------------------------------------------------------------------------------------------------------


 





