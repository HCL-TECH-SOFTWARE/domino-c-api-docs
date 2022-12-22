




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



**Function : Compound Text**



**CompoundTextAddRenderedNote** **- Renders a
note into Composite Data format and adds it to a CompoundText context.**


**----------------------------------------------------------------------------------------------------------**



**#include <easycd.h>**



STATUS
LNPUBLIC **CompoundTextAddRenderedNote(**  

      DHANDLE  hCompound,  

      NOTEHANDLE  hNote,  

      NOTEHANDLE  hFormNote,  

      DWORD  dwFlags**);**



**Description :**



This
function takes as input a CompoundText context handle and a note handle. The
function will render the specified note in Composite Data format(i.e.,
richtext) and add the rendered note to the CompoundText context.  This allows
an editable copy of an entire note to be embedded in another note.


 


**Parameters :**



Input :  

hCompound  -  The handle of the CompoundText context that will contain the
rendered note.  

  

hNote  -  The handle of the note that is to be rendered.  

  

hFormNote  -  The handle of the form note to use to render the note.  If
NULLHANDLE is specified, and note to be rendered contains a FIELD\_FORM item,
the FIELD\_FORM form will be used to render the note. If NULLHANDLE is specified
and the note does not contain a FIELD\_FORM, then the database's default form
will be used.  

  

dwFlags  -  Reserved - must be 0.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully added the rendered note to the CompoundText context.  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  




 **See Also :**


**[CompoundTextAddDocLink](CompoundTextAddDocLink.md)**


**[CompoundTextAddParagraphExt](CompoundTextAddParagraphExt.md)**


**[CompoundTextAddTextExt](CompoundTextAddTextExt.md)**


**[CompoundTextCreate](CompoundTextCreate.md)**


**[CompoundTextDefineStyle](CompoundTextDefineStyle.md)**


**[CompoundTextInitStyle](CompoundTextInitStyle.md)**



----------------------------------------------------------------------------------------------------------


 





