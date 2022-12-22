




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 7.0.2**



**Function : MIME**



**MMSetReadReceipt** **- set
Conversion Controls read receipt setting**


**----------------------------------------------------------------------------------------------------------**



**#include <mailmisc.h>**



void
LNPUBLIC **MMSetReadReceipt(**  

      CCHANDLE  hCC,  

      WORD  wReadReceipt**);**



**Description :**



The
function  MMSetReadReceipt sets the Conversions Controls read receipt setting
to the input value, wReadReceipt.  No checking is done for out of bounds
values.


 


**Parameters :**



Input :  

hCC  -  a handle to a Conversion Controls context from a previous call to
MMCreateConvControls.  

  

wReadReceipt  -  the value to use for the Conversion Controls read receipt
setting.  

  




Output :  

(routine)  -  void  

  

  




 **Sample Usage :**


MMSetReadReceipt(hCC,
0);     /\*  0 - Do not pass read receipt requests when importing or exporting 


                              1
- Support read receipt requests (as Return-Receipt-To when exporting)


                              2
- Support read receipt requests (as Disposition-Notification-To when exporting)
\*/


 


 **See Also :**


**[MMGetReadReceipt](MMGetReadReceipt.md)**


**[CCHANDLE](CCHANDLE.md)**



----------------------------------------------------------------------------------------------------------


 





