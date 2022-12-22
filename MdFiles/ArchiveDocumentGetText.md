




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



**ArchiveDocumentGetText** **- Converts
an item in an archive document to text.**


**----------------------------------------------------------------------------------------------------------**



**#include <archsvc.h>**



STATUS
LNPUBLIC **ArchiveDocumentGetText(**  

      HARCHIVEDOCUMENT  hArchDoc,  

      const char \*ItemName,  

      DWORD  NameLen,  

      ARCHIVETEXTOUTPUTCALLBACK  ArchiveTextOutputCallback,  

      void \*pUserCtx**);**



**Description :**



Just for
supported types see NSFItemConvertToText. As well, all MIME subtypes of type
text (i.e text/plain, text/html) are returned when an item contains MIME.


 


**Parameters :**



Input :  

hArchDoc  -  Handle to ArchiveDocument.  

  

ItemName  -  Name of the item to convert. Corresponds to item name in
originating notes document.  

  

NameLen  -  Length of ItemName.  

  

ArchiveTextOutputCallback  -  Callback function that receives data.  

  

pUserCtx  -  Caller-defined context structure.  

  




Output :  

(routine)  -  NOERROR return status means that it is successful.  

  

  




 **See Also :**


**[ARCHIVETEXTOUTPUTCALLBACK](ARCHIVETEXTOUTPUTCALLBACK.md)**



----------------------------------------------------------------------------------------------------------


 





