




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



**ARCHIVEDOCUMENTCALLBACK** **-** User-defined
function called by ArchiveExportDatabase that used to pass an archive document
to the implementor.


**----------------------------------------------------------------------------------------------------------**



**#include
<archsvc.h>**



**Definition :**



typedef STATUS
(LNCALLBACKPTR ARCHIVEDOCUMENTCALLBACK)


               (


               HARCHIVEDOCUMENT
hArchDoc,


               void
\*pUserCtx);


 


**Description :**



Implementors
must call ArchiveDocumentDestroy when finished to free resources.


 


            Inputs:



                        hArchDoc
- Handle to archive document.


 
                     pUserCtx - Caller-defined context structure. 


      
Return:


             
NOERROR return status means that it is successful.


 **See Also :**


**[ArchiveDocumentExport](ArchiveDocumentExport.md)**


**[ArchiveExportDatabase](ArchiveExportDatabase.md)**



----------------------------------------------------------------------------------------------------------


 





