




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



**DirEntryItemAdd** **-
Overwrites the values of an entry item.** 


**----------------------------------------------------------------------------------------------------------**



**#include <direntry.h>**



STATUS
LNPUBLIC **DirEntryItemAdd(**  

      DIRENTRY  hEntry,  

      const char \*itemName,  

      WORD  itemDataType,  

      const void \*itemVal,  

      DWORD  itemValLen**);**



**Description :**



If the item
does not exist then it is created. If it does already exist then its values are
replaced. 


        Note
that this routine only affects the in-memory hEntry object. The changes are
written to the directory entry only after a subsequent DirEntryUpdate()[E:\temp\dir\html\direntry\_8h.html
- 8ebb95936adba73844deb8acbdd86f82](file:///E:/temp/dir/html/direntry_8h.html#8ebb95936adba73844deb8acbdd86f82) operation on the hEntry.


 


**Parameters :**



Input :  

hEntry  -  Handle to the entry whose item is to be modified.  

  

itemName  -  Name of the item to be added.  

  

itemDataType  -  The Notes data type of the new itemVal. See the section on
Data Types for more information.  

  

itemVal  -  Value to be added for itemName.  

  

itemValLen  -  Size of itemVal in bytes.  

  




Output :  

(routine)  -  NOERROR   

ERR\_DIR\_NULL\_ARGUMENT   

If hEntry, itemName, or itemVal are NULL.   

...   

An ERR status on failure indicating the problem.   

  

  

  




 **See Also :**


**[DirEntryDelete](DirEntryDelete.md)**


**[DirEntryFree](DirEntryFree.md)**


**[DirEntryItemDelete](DirEntryItemDelete.md)**


**[DirEntryUpdate](DirEntryUpdate.md)**



----------------------------------------------------------------------------------------------------------


 





