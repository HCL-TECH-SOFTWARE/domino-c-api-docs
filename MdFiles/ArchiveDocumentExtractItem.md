




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



**ArchiveDocumentExtractItem** **- Removes
an item from an ArchiveDocument and returns the value to the caller.**


**----------------------------------------------------------------------------------------------------------**



**#include <archsvc.h>**



STATUS
LNPUBLIC **ArchiveDocumentExtractItem(**  

      HARCHIVEDOCUMENT  hArchDoc,  

      const char \*ItemName,  

      WORD  NameLen,  

      ITEMEXTRACTCALLBACK  ItemExtractCallback,  

      void \*pUserCtx**);**



**Description :**



Item(s) must
be returned to the archive document using ArchiveDocumentInsertItem before the
document can be restored to a database. See ArchiveDocumentRestore for more
details on restoring a document to a database.


 


**Parameters :**



Input :  

hArchDoc  -  Handle to ArchiveDocument.  

  

ItemName  -  Name of the item to extract. Corresponds to item name in
originating notes document. If there are multiple items with the same name all
will be concatenated together and passed to the caller.   

  

NameLen  -  Length of ItemName.  

  

ItemExtractCallback  -  Callback function that receives data. Note that data
format passed to this function is opaque.  

  

pUserCtx  -  Caller-defined context structure.  

  




Output :  

(routine)  -  ERR\_ITEM\_NOT\_FOUND if there is no item with matching name.
NOERROR if successful, error status     from lower level functions otherwise.  

  

  




 **See Also :**


**[ITEMEXTRACTCALLBACK](ITEMEXTRACTCALLBACK.md)**



----------------------------------------------------------------------------------------------------------


 





