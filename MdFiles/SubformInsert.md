




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



**SubformInsert** **- Insert
subform into form or subform design note.**


**----------------------------------------------------------------------------------------------------------**



**#include <easycd.h>**



STATUS
LNPUBLIC **SubformInsert(**  

      DBHANDLE  hDB,  

      char \*pSubForm,  

      char \*pForm,  

      DWORD  Flags**);**



**Description :**



This
function appends a subform to another form or subform.  Please see Chapter 8-1
Forms in the *User Guide* for information on how to create a subform.


 


**Parameters :**



Input :  

hDB  -  Handle to the database.  

  

pSubForm  -  Subform name to attach.  

  

pForm  -  Parent form name or subform name that will contain the inserted
subform.  

  

Flags  -  Subforms are implemented as a hotspot.  You may specify some of the
hotspot attributes with this parameter.  This would be equivalent to setting
the Flags member of a CDHOTSPOTBEGIN record.   See HOTSPOTREC\_RUNFLAG\_xxx  for
possible values.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_xxx - Errors returned by lower level Notes functions.  There are so many
possible causes, that it is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  




 **See Also :**


**[SubformRemove](SubformRemove.md)**


**[HOTSPOTREC\_RUNFLAG\_xxx](HOTSPOTREC_RUNFLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





