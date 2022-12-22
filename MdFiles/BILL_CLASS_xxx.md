




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



**BILL\_CLASS\_xxx** **-** Billing
Classes


**----------------------------------------------------------------------------------------------------------**



**#include <billing.h>**


 **Symbolic Values :**      BILL\_CLASS\_SESSION        -  Session billing class  

  

      BILL\_CLASS\_REPLICATION            -  Replication billing class  

  

      BILL\_CLASS\_DOCUMENT   -  Document billing class  

  

      BILL\_CLASS\_MAIL   -  Mail billing class  

  

      BILL\_CLASS\_DATABASE     -  Database billing class  

  

      BILL\_CLASS\_AGENT           -  Agent billing class  

  

      BILL\_CLASS\_HTTPREQUEST          -  Http Request billing class  

  




**Description :**



The above
constants provide unique billing class values.   They can be bitwise OR'ed with
a billing class mask, as returned by the BillingGetClass() function, to
determine the active classes on the billing server.


 **See Also :**


**[BillingGetClass](BillingGetClass.md)**



----------------------------------------------------------------------------------------------------------


 





