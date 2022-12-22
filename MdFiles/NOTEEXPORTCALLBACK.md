




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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



**Data Type : archiving service**



**NOTEEXPORTCALLBACK** **-** User defined
callback function for receiving notes document data.


**----------------------------------------------------------------------------------------------------------**



**#include
<archsvc.h>**



**Definition :**



typedef STATUS
(LNCALLBACKPTR NOTEEXPORTCALLBACK)


               (


               const
BYTE \*Buffer,


               DWORD
dwBufferSize,


               BOOL
bLastBuffer, 


               STATUS
retError,


               void
\*pUserCtx


               );


 


**Description :**



Note that
the format of document data is opaque and suitable for external storage. Use
ArchiveImportDocument to restore to an in-memory note for access to individual
items. 


 


            Inputs:


                        Buffer
- Contains a serialized notes document (or a partial stream depending on the
size).


                        BufferSize
- Size of Buffer. 


                        bLastBuffer
- When TRUE, indicates that this is the last buffer of data for the current
note.


                        pUserCtx
- Caller-defined context structure.  


            Returns:


                        NOERROR
if successful, error status from lower level functions otherwise.


 **See Also :**


**[ArchiveDocumentExport](ArchiveDocumentExport.md)**



----------------------------------------------------------------------------------------------------------


 





