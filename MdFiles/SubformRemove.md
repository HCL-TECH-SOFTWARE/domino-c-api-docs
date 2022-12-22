




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



**Function : Form**



**SubformRemove** **- Remove a
subform from a form or subform design note.**


**----------------------------------------------------------------------------------------------------------**



**#include <easycd.h>**



STATUS
LNPUBLIC **SubformRemove(**  

      DBHANDLE  hDB,  

      char \*pSubForm,  

      char \*pForm,  

      DWORD  Flags**);**



**Description :**



This
function removes a subform from a form or subform.


 


**Parameters :**



Input :  

hDB  -  Handle to the database.  

  

pSubForm  -  Subform name to remove.  

  

pForm  -  Parent form name or subform name from which the specified subform is
to be removed.  

  

Flags  -  Reserved for future use.  Specify  0L.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **See Also :**


**[SubformInsert](SubformInsert.md)**



----------------------------------------------------------------------------------------------------------


 





