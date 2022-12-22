




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



**Function : Billing**



**BillingGetClass** **- Gets the
active Billing Class mask**


**----------------------------------------------------------------------------------------------------------**



**#include <billing.h>**



STATUS
LNPUBLIC **BillingGetClass(**  

      DWORD far \*BillingClass**);**



**Description :**




BillingGetClass()
supplies a 32-bit mask that specifies which billing classes are active on the
billing server.  This information is derived from the notes.ini  BillingClass
variable.  This mask value can be bitwise OR'ed with the BILL\_CLASS\_xxx symbols
to interpret the active classes. 


 


Only a
billing server task can execute BillingGetClass().  This call is a convenience
for programs using the BillingWrite() function.  It is not necessary to use
this call when extracting data from the MQ$Billing message queue.


 


**Parameters :**



Input :  

BillingClass  -  Address of the 32-bit Billing Class mask.  

  




Output :  

(routine)  -  If message is obtained successfully; NOERROR;  

If the notes.ini BillingClass variable is not present; ERR\_BAD\_PARAM.  

  

  

BillingClass  -  The active Billing Class mask, that can be logically OR'ed
with BILL\_CLASS\_xxx.  

  




 **See Also :**


**[BILL\_CLASS\_xxx](BILL_CLASS_xxx.md)**


**[BillingWrite](BillingWrite.md)**



----------------------------------------------------------------------------------------------------------


 





