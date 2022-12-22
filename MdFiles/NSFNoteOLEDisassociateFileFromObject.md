




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




**Initial Release 6**



**Function : OLE**



**NSFNoteOLEDisassociateFileFromObject** **-
Disassociate an attachment ($FILE) from an OLE object.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfasc.h>**



STATUS
LNPUBLIC **NSFNoteOLEDisassociateFileFromObject(**  

      NOTEHANDLE  hNote,  

      char \*pszObjName,  

      char \*pszAttachmentName**);**



**Description :**



Disassociate
an attachment ($FILE) from an OLE object.


 


**Parameters :**



Input :  

hNote  -  Handle of the OLE object's note.  

  

pszObjName  -  Pointer to name of the OLE object.  

  

pszAttachmentName  -  Pointer to the name of the attachment to disassociate.  

  




Output :  

(routine)  -  Return indicates either success or what the error is. The return
codes include:   

  

NOERROR - Operation was successful.  

  

ERR\_ARGS\_INVALID - A required argument (hNote, pszObjName, pszAttachmentName)
was not supplied.  

  

ERR\_ASSOCITEM\_NOITEMS - There are no files associated with the OLE object.  

  

ERR\_xxx - STATUS returned from a lower level Notes function call.  Use
OSLoadString and display/log the error.  

  

  




 **See Also :**


**[NSFNoteOLEAssociateFileToObject](NSFNoteOLEAssociateFileToObject.md)**


**[NSFNoteOLEGetAssociateFileOnObject](NSFNoteOLEGetAssociateFileOnObject.md)**



----------------------------------------------------------------------------------------------------------


 





