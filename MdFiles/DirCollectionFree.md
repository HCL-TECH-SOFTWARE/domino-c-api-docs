




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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



**DirCollectionFree** **- Free the
memory associated with a collection of entries returned by a search operation.**


**----------------------------------------------------------------------------------------------------------**



**#include <dircoll.h>**



void
LNPUBLIC **DirCollectionFree(**  

      DIRCOLLECTION  hCollection**);**



**Description :**



This function
calls DirEntryFree(),deallocating each of the directory entries in this
collection.


 


**Parameters :**



Input :  

hCollection  -  Handle to the collection of entries to free. If
NULLDIRCOLLECTION then nothing is freed.  

  




Output :  

(routine)  -  This function returns a VOID,if the free fails a
NULLDIRCOLLECTION is returned in the parameter.  

  

  




 **See Also :**


**[DIRCOLLECTION](DIRCOLLECTION.md)**


**[DirCollectionFirstEntry](DirCollectionFirstEntry.md)**


**[DirCollectionGetNumEntries](DirCollectionGetNumEntries.md)**


**[DirCollectionNextEntry](DirCollectionNextEntry.md)**


**[DirCollectionNthEntry](DirCollectionNthEntry.md)**


**[DirCollectionPrint](DirCollectionPrint.md)**



----------------------------------------------------------------------------------------------------------


 





