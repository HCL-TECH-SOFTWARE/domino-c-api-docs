




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




**Initial Release 6.5.3**



**Function : Note**



**NSFNoteSignHotspots** **- Sign the
source and object code associated with the hotspots on a document.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteSignHotspots(**  

      NOTEHANDLE  hNote,  

      DWORD  dwFlags,  

      BOOL \*retfSigned**);**



**Description :**



This
function will sign all hotspots in a document that contain object code.  Using
the current ID, signature data will be added to any signature containing CD
records for hotspots having code within TYPE\_COMPOSITE items. 


 


This routine
only operates on documents.  If the note is a design element, the routine
returns NOERROR without signing anything.


 


**Parameters :**



Input :  

hNote  -  The handle of an open note.  

  

dwFlags  -  Reserved for future use.  Should be set to ZERO.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - The hotspots were successfully signed.  

ERR\_xxx - STATUS returned from a lower level Notes function.  This value can be
passed to OSLoadString to obtain a text string that can be presented in a
dialog box or log entry.  

  

  

retfSigned  -  TRUE if any hotspots are signed, otherwise FALSE.  Set to NULL
if this information is not needed.  

  




 **See Also :**


**[NSFHotSpotSign](NSFHotSpotSign.md)**



----------------------------------------------------------------------------------------------------------


 





