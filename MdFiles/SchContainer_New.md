




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



**SchContainer\_New** **- Allocate
a new object container.**


**----------------------------------------------------------------------------------------------------------**



**#include <schedule.h>**



STATUS
LNPUBLIC **SchContainer\_New(**  

      HCNTNR FAR \*rethCntnr**);**



**Description :**



This routine
allocates a new Calendaring and Scheduling object container.


 


**Parameters :**




Output :  

(routine)  -  NOERROR - Successfully allocated a new container.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

  

rethCntnr  -  Returns a handle to the object container.  

  




 **See Also :**


**[SchContainer\_Free](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1B1F99C51F7DAA688525635D006DEB1C)**



----------------------------------------------------------------------------------------------------------


 





