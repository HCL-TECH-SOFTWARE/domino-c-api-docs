




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



**Symbolic Value : Billing**



**BILLCHARGExxx** **-** Document
Billing type


**----------------------------------------------------------------------------------------------------------**



**#include <billing.h>**


 **Symbolic Values :**      BILLCHARGEREAD              -  Indicates the billing server
accessed a $ChargeRead field in a document.  

  

      BILLCHARGEWRITE            -  Indicates the billing server accessed a
$ChargeWrite field in a document.  

  




**Description :**



These two
constants identify the type of document operation that generated the billing
record.  They are assigned to the Type parameter of the DOCUMENT billing
record.


 


      For
more information, see the *Domino 5 Administration Help* documentation.


 **See Also :**


**[BillingWrite](BillingWrite.md)**


**[DOCUMENT](DOCUMENT.md)**



----------------------------------------------------------------------------------------------------------


 





