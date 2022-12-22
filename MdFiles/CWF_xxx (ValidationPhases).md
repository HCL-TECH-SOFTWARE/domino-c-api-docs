




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



**CWF\_xxx (Validation Phases)** **-** Validation
phases of NSFNoteComputeWithForm.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**


 **Symbolic Values :**      CWF\_DV\_FORMULA            -  Error occurred when processing
the Default Value formula.  

  

      CWF\_IT\_FORMULA             -  Error occurred when processing the
Translation formula.  

  

      CWF\_IV\_FORMULA             -  Error occurred when processing the
Validation formula.  

  

      CWF\_COMPUTED\_FORMULA         -  Error occurred when processing the
computed field Value formula.  

  

      CWF\_DATATYPE\_CONVERSION     -  Error occurred when verifying the data
type for the field.  

  

      CWF\_COMPUTED\_FORMULA\_LOAD           -  Error occurred when processing the
computed field Value formula, during the "load" pass.  

  

      CWF\_COMPUTED\_FORMULA\_SAVE           -  Error occurred when processing the
computed field Value formula, during the "save" pass.  

  




**Description :**



The
validation phase value is passed to the error callback routine CWF\_ERROR\_PROC
(called by NSFNoteComputeWithForm()).  These values indicate the phase of the
validation process where the error was encountered.


 


**Note:**


The
NSFNoteComputeWithForm API function has a two pass validation process:  The
"load" pass runs the default field value and related computed field
value formulas. The "save" pass runs the translation, validation, and
datatype input field formulas, along with the related computed field value
formulas.  Since computed field values are validated for both passes, the error
callback function can be called twice for the relevant fields.   Future
releases of the Lotus C API for Domino and Notes will expand the validation
phases to include the pass that the error occurred in.


 **See Also :**


**[CWF\_ERROR\_PROC](CWF_ERROR_PROC.md)**


**[CWF\_xxx (Return Codes)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/70D2C510DEF69C6C85256261005D9C2B)**


**[NSFNoteComputeWithForm](NSFNoteComputeWithForm.md)**



----------------------------------------------------------------------------------------------------------


 





