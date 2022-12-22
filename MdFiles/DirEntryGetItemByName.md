




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
@font-face
 {font-family:Calibri;
 panose-1:2 15 5 2 2 2 4 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
a:link, span.MsoHyperlink
 {color:#0563C1;
 text-decoration:underline;}
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




**Initial Release 8.5.2**



**Function : Dir**



**DirEntryGetItemByName** **- Get the
value(s) of an item in an entry based on the item name.** 


**----------------------------------------------------------------------------------------------------------**



**#include <direntry.h>**



STATUS
LNPUBLIC **DirEntryGetItemByName(**  

      DIRENTRY  hEntry,  

      const char \*itemName,  

      WORD \*pItemDataType,  

      DHANDLE \*phItemValue,  

      DWORD \*pItemValLen**);**



**Description :**



Note that
this routine must first determine the index of the item corresponding to
itemName in order to get the value of that item. For this reason it is slower
that DirEntryGetItem(), which can access the value directly with the index
provided by the caller. Callers are encouraged to use DirEntryGetItem()[E:\temp\dir\html\direntry\_8h.html
- 3f34426ead87c0912d246c5a17d113f5](file:///E:/temp/dir/html/direntry_8h.html#3f34426ead87c0912d246c5a17d113f5) whenever possible.


 


**Parameters :**



Input :  

hEntry  -  Handle to the entry whose item is to be returned. If hEntry is
NULLDIRENTRY then NULL is returned.  

  

itemName  -  The name of the item to get.  

  




Output :  

(routine)  -    

NOERROR   

  

  

  

ERR\_NO\_SUCH\_ITEM   

If item was not requested in Search.   

  

ERR\_DIR\_NULL\_ENTRY   

If hEntry is NULL.   

  

ERR\_DIR\_NULL\_ARGUMENT   

If itemName is NULL.   

  

...   

An ERR status on failure indicating the problem.   

  

  

  

pItemDataType  -  The Notes data type of the item. See the section on Data
Types.  

  

phItemValue  -  handle is returned to the memory containing the value. This
memory is allocated for the caller and is up to the caller to free. Note if the
item value is 0, this handle will be returned NULL  

  

pItemValLen  -  The size of the value(s) for itemName in bytes.  

  




 **See Also :**


**[DirEntryGetItem](DirEntryGetItem.md)**



----------------------------------------------------------------------------------------------------------


 





