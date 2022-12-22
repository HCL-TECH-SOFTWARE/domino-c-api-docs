




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



**NSFNoteOLEAssociateFileToObject** **- Associate
an attachment ($FILE) with an OLE object.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfasc.h>**



STATUS
LNPUBLIC **NSFNoteOLEAssociateFileToObject(**  

      NOTEHANDLE  hNote,  

      char \*pszObjName,  

      char \*pszFileSpec,  

      char \*pszAttachmentName,  

      WORD  wIfExists,  

      DWORD  dwFlags,  

      DWORD \*pdwId**);**



**Description :**



The
association can be made using an existing associated $FILE or can create a new
$FILE from a system file and then create the association.  If there is no file
spec, but there is an attachment name and the attachment exists, use existing
attachment for association.


 


**Parameters :**



Input :  

hNote  -  Handle of the OLE object's note.  

  

pszObjName  -  Pointer to name of the OLE object in the note.  

  

pszFileSpec  -  Pointer to the file specification of the file to associate with
the object (see NSFNoteAttachFile - file\_name for details).  If attachment
already exists, set this to NULL.  

  

pszAttachmentName  -  Pointer to the name of the attachment to associate.  

  

wIfExists  -  see ASSOCITEM\_IFEXISTS\_xxx  

  

dwFlags  -  Currently not used.  

  




Output :  

(routine)  -  Return indicates either success or what the error is. The return
codes include:   

  

NOERROR - Operation was successful.  

  

ERR\_ARGS\_INVALID - A required argument (hNote, pszObjName, pszAttachmentName)
was not supplied.  

  

ERR\_ASSOCITEM\_ATTACHMENT - A required argument (pszFileSpec) was not supplied.  

  

ERR\_ASSOCITEM\_ATTACHMENT\_ITEM\_EXISTS - File attachment already exists.  

  

ERR\_xxx - STATUS returned from a lower level Notes function call.  Use
OSLoadString and display/log the error.  

  

  

pdwId  -  Pointer to the location which contains the Id of the associated
$FILE.  

  




 **See Also :**


**[ASSOCITEM\_IFEXISTS\_xxx](ASSOCITEM_IFEXISTS_xxx.md)**


**[NSFNoteAttachFile](NSFNoteAttachFile.md)**


**[NSFNoteOLEDisassociateFileFromObject](NSFNoteOLEDisassociateFileFromObject.md)**


**[NSFNoteOLEGetAssociateFileOnObject](NSFNoteOLEGetAssociateFileOnObject.md)**



----------------------------------------------------------------------------------------------------------


 





