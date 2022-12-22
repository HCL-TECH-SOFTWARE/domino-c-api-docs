




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




**Initial Release 5.0.9**



**Function : Form**



**StoredFormAddItems** **- Add form
and subform design note items to a data note to support "store form with
note" functionality.**


**----------------------------------------------------------------------------------------------------------**



**#include <dbmisc.h>**



STATUS
LNPUBLIC **StoredFormAddItems(**  

      DBHANDLE  hSrcDbHandle,  

      DHANDLE  hSrcNote,  

      DHANDLE  hDstNote,  

      BOOL  bDoSubforms,  

      DWORD  dwFlags**);**



**Description :**



This
function adds form and subform design note items to a data note to support
"store form with note" functionality.


 


**Parameters :**



Input :  

hSrcDbHandle  -  Handle of the database containing the design note of the form
whose items are to be added to the destination data note.  

  

hSrcNote  -  Note handle of the form's design note to copy items from.  

  

hDstNote  -  Note handle of the data note to copy design note items to.  

  

bDoSubforms  -  Copy items from design notes of all subforms used by form.  

  

dwFlags  -  Reserved for future use. Should be 0  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_xxx - Errors returned by lower level functions.  Call OSLoadString to
interpret the error code for display.  

  

  




 **See Also :**


**[StoredFormAppendSubformToken](StoredFormAppendSubformToken.md)**


**[StoredFormRemoveItems](StoredFormRemoveItems.md)**



----------------------------------------------------------------------------------------------------------


 





