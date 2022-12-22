




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



**ITEMEXTRACTCALLBACK** **-** User defined
callback function for receiving item data from an archive document. 


**----------------------------------------------------------------------------------------------------------**



**#include
<archsvc.h>**



**Definition :**



typedef STATUS
(LNCALLBACKPTR ITEMEXTRACTCALLBACK)


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
the format of the item data exported is opaque and suitable for external
storage.


 


            Inputs:


                        Buffer
- Contains a serialized item data.


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


**[ArchiveDocumentExtractItem](ArchiveDocumentExtractItem.md)**



----------------------------------------------------------------------------------------------------------


 





