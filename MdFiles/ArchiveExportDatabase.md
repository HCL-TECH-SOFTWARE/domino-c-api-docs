




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



**ArchiveExportDatabase** **- Exports a
set of documents from a database to user supplied callbacks.** 


**----------------------------------------------------------------------------------------------------------**



**#include <archsvc.h>**



STATUS
LNPUBLIC **ArchiveExportDatabase(**  

      DBHANDLE  hDb,  

      DHANDLE  hIDTable,  

      DWORD  Flags,  

      NOTEINITCALLBACK  NoteInitCallback,  

      ARCHIVEATTACHINIT  AttachInitCallback,  

      ARCHIVEATTACHOUTPUT  AttachOutputCallback,  

      ARCHIVEDOCUMENTCALLBACK  ArchiveDocumentCallback,  

      KFHANDLE  hKFC,  

      void \*pUserCtx**);**



**Description :**



The
ArchiveExportDatabase function copies notes and their related attachments from
a database and passes the exported data to callers via a set of callback
functions. Callbacks occur in the order that they appear in the function
declaration. Attachments are decompressed so that they may be consumed by
programs that understand their native format. Notes documents are encoded into
a canonical format that is opaque to the caller but can be manipulated in a
limited way by the Archiving Services API. 


 


**Parameters :**



Input :  

hDb  -  Handle to source database.  

  

hIDTable  -  Handle to IDTable indicating the notes to be exported.  

  

Flags  -  Flags that control optional behavior (None defined at this point).  

  

NoteInitCallback  -  Called for every note that is streamed to the caller.
Gives the implementor an opportunity to allocate space, etc. needed for the
data.  

  

AttachInitCallback  -  User supplied callback that is called to indicate that a
file attachment is being sent.   

  

AttachOutputCallback  -  User supplied callback that receives attachment data.  

  

ArchiveDocumentCallback  -  User supplied callback that receives a Notes
document in stream format.(See NOTEEXPORTCALLBACK for more details)  

  

hKFC  -  Needed to decrypt encrypted notes. Handle for ID File. Pass null for
current user ID.  

  

pUserCtx  -  Caller-defined context structure.  

  




Output :  

(routine)  -  NOERROR if successful, error status from lower level functions
otherwise.  

  

  




 **See Also :**


**[ARCHIVEATTACHINIT](ARCHIVEATTACHINIT.md)**


**[ARCHIVEATTACHOUTPUT](ARCHIVEATTACHOUTPUT.md)**


**[ARCHIVEDOCUMENTCALLBACK](ARCHIVEDOCUMENTCALLBACK.md)**


**[NOTEINITCALLBACK](NOTEINITCALLBACK.md)**



----------------------------------------------------------------------------------------------------------


 





