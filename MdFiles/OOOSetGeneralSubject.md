




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




**Initial Release 8.5.2**



**Function : OOO**



**OOOSetGeneralSubject** **- This
function sets general subject messages.**


**----------------------------------------------------------------------------------------------------------**



**#include <oooapi.h>**



STATUS
LNPUBLIC **OOOSetGeneralSubject(**  

      OOOCTXPTR \*pOOOContext,  

      const char \*pGeneralSubject,  

      BOOL  bDisplayReturnDate**);**



**Description :**



OOO supports
two sets of notification messages.  They are called General message/subject and
Special message/subject.The rest of the people will receive the general
message/subject message. This function sets the general subject.If this field
is not specified in by this API call, the value defined using Notes Client will
be used, otherwise the default for this field is the following text


*AUTO:
Katherine Smith is out of the office (returning 02/23/2009 10:12:17 AM)*



**Parameters :**



Input :  

pOOOContext  -  Pointer obtained from the OOOStartOperation call   

  

pGeneralSubject  -  This is a pointer to a zero terminated string that will
appear as the subject line of the OOO notification.  

  

bDisplayReturnDate  -  This is a Boolean which controls whether ("returning
<date>") appears on the subject line.  Default value is TRUE.  

  




Output :  

(routine)  -  This is a Boolean which controls whether ("returning <date>")
appears on the subject line.  Default value is TRUE.  

  

  




 **See Also :**


**[OOOGetGeneralSubject](OOOGetGeneralSubject.md)**



----------------------------------------------------------------------------------------------------------


 





