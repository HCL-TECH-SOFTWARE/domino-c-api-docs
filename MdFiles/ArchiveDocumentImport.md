




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



**ArchiveDocumentImport** **- Creates
an ArchiveDocument from a previously exported stream.**


**----------------------------------------------------------------------------------------------------------**



**#include <archsvc.h>**



STATUS
LNPUBLIC **ArchiveDocumentImport(**  

      DWORD  Flags,  

      NOTEIMPORTCALLBACK  NoteImportCallback,  

      void \*pUserCtx,  

      HARCHIVEDOCUMENT \*phArchDoc**);**




**Parameters :**



Input :  

Flags  -  Unused. Please set 0.  

  

NoteImportCallback  -  Caller defined function that returns exported note data
in the supplied buffer.  

  

pUserCtx  -  Caller-defined context structure.  

  




Output :  

(routine)  -  NOERROR if successful, error status from lower level functions
otherwise.  

  

  

phArchDoc  -  Pointer to created ArchiveDocument. Callers should free the
created document with ArchiveDocumentDestroy.  

  




 **See Also :**


**[ArchiveRestoreDocument](ArchiveRestoreDocument.md)**


**[ArchiveRestoreDocumentToNote](ArchiveRestoreDocumentToNote.md)**


**[NOTEIMPORTCALLBACK](NOTEIMPORTCALLBACK.md)**



----------------------------------------------------------------------------------------------------------


 





