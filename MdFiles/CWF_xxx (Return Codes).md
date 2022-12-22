




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



**Symbolic Value : Note**



**CWF\_xxx (Return Codes)** **-** Return codes
for callback routine called by NSFNoteComputeWithForm().


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**


 **Symbolic Values :**      CWF\_ABORT           -  End all processing by
NSFNoteComputeWithForm() and return the error status to the caller.  

  

      CWF\_NEXT\_FIELD   -  End validation of the current field and go on to the
next.  

  

      CWF\_RECHECK\_FIELD       -  Begin the validation process for this field
over again.  

  




**Description :**



These are
the values that may be returned from the callback function CWF\_ERROR\_PROC
(called from NSFNoteComputeWithForm()).  The value returned will determine the
subsequent processing.


 **See Also :**


**[CWF\_ERROR\_PROC](CWF_ERROR_PROC.md)**


**[CWF\_xxx (Validation Phases)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E2F5A18E435B5FE985256237005182EE)**


**[NSFNoteComputeWithForm](NSFNoteComputeWithForm.md)**



----------------------------------------------------------------------------------------------------------


 





