




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




**Initial Release 8.5.2**



**Function : Dir**



**DirEntryGetItem** **- Get the
value(s) of an item in an entry based on the item index.** 


**----------------------------------------------------------------------------------------------------------**



**#include <direntry.h>**



STATUS
LNPUBLIC  **DirEntryGetItem(**  

      const DIRENTRY  hEntry,  

      WORD  itemIndex,  

      char \*itemName,  

      WORD \*itemDataType,  

      DHANDLE \*hItemValue,  

      DWORD \*itemValLen**);**



**Description :**



Get the
value(s) of an item in an entry based on the item index. 


         
Note that callers are encouraged to use this routine rather than
DirEntryGetItemByName(),since it is faster (because of the way the result
buffer is arranged). 


         
Note that this function's status code will reveal if the item exists or not
even if the caller passes in a NULL hItemValue.


 


**Parameters :**



Input :  

hEntry  -  Handle to the entry whose item is to be returned. If hEntry is
NULLDIRENTRY then NULL is returned.  

  

itemIndex  -  The index of the item whose value is to be returned. The index
position of items is determined by the order the items were asked for on the
search or get operation that returned the entry.  

  




Output :  

(routine)  -    

NOERROR   

  

ERR\_NO\_SUCH\_ITEM   

If item was not requested in Search.   

  

ERR\_DIR\_NULL\_ENTRY   

If hEntry is NULL.   

  

...   

An ERR status on failure indicating the problem.   

  

  

  

itemName  -  The name of the item returned. The caller must supply a buffer of
at least ITEM\_NAME\_MAX+1 bytes, in which the name of the item will be returned.
Specify NULL if not desired.  

  

itemDataType  -  The Notes data type of the item. The possible values returned
are the following, taken from nsfdata.h   

TYPE\_TEXT, TYPE\_TEXT\_LIST: Use DirEntryGetTextItem() to get a value   

TYPE\_NUMBER, TYPE\_NUMBER\_RANGE: Use DirEntryGetNumberItem() to get a value   

TYPE\_TIME, TYPE\_TIME\_RANGE: Use DirEntryGetTimeItem() to get a value  

  

hItemValue  -  A handle is returned to the memory containing the value. This
memory is allocated for the caller and is up to the caller to free. Note if the
item value is 0, this handle will be returned NULL  

  

itemValLen  -  The size of the value(s) for itemName in bytes.  

  




 **See Also :**


**[DirEntryGetItemByName](DirEntryGetItemByName.md)**



----------------------------------------------------------------------------------------------------------


 





