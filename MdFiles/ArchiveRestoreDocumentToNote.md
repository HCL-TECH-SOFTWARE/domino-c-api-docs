




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




**Initial Release 8.5**



**Function : archiving service**



**ArchiveRestoreDocumentToNote** **- Returns
an exported notes document to an open note.**


**----------------------------------------------------------------------------------------------------------**



**#include <archsvc.h>**



STATUS
LNPUBLIC **ArchiveRestoreDocumentToNote(**  

      NOTEHANDLE  hTargetNote,  

      DWORD  Flags,  

      HARCHIVEDOCUMENT  hArchDoc,  

      void \*pUserCtx**);**



**Description :**



ArchiveRestoreDocumentToNote
returns the exported note data to an open note supplied by the caller. It does
not restore attachments and thus care needs to be taken to ensure that either
the note is not saved to the database or attachments are restored and
references to attachments in the note are adjusted accordingly.


 


**Parameters :**



Input :  

hTargetNote  -  Handle to target note.  

  

Flags  -  Unused. Please set 0.  

  

hArchDoc  -  Handle to archive document. See ArchiveDocumentImport for details
on obtaining an archive document handle.  

  

pUserCtx  -  Caller-defined context structure.   

  




Output :  

(routine)  -  NOERROR if successful, error status ERR\_ARCHIVE\_IMPORT\_UNEXPECTED\_EOD
if incomplete data stream returned. from lower level functions otherwise.  

  

  




 **See Also :**


**[ArchiveDocumentImport](ArchiveDocumentImport.md)**


**[HARCHIVEDOCUMENT](HARCHIVEDOCUMENT.md)**



----------------------------------------------------------------------------------------------------------


 





