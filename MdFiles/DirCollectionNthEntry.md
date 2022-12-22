




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



**DirCollectionNthEntry** **- Find the
Nth entry in the hCollection collection.**


**----------------------------------------------------------------------------------------------------------**



**#include <dircoll.h>**



DIRENTRY
LNPUBLIC **DirCollectionNthEntry(**  

      DIRCOLLECTION  hCollection,  

      DWORD  N**);**



**Description :**



Find the Nth
entry in the hCollection collection.


 


**Parameters :**



Input :  

hCollection  -  Handle to the collection of entries to be navigated.  

  

N  -  The n-th  

  




Output :  

(routine)  -  A reference to the N-th match in hCollection. This does not use
or update the collection's internally maintained "current" directory
entry cursor. If the input hCollection is NULLDIRCOLLECTION, or N is out of
bounds, or the Nth entry has already been freed, then the return value is NULLDIRENTRY.
  

DirEntryFree() may be called on the returned directory entry object to remove
it from the collection. Or, the entry will be freed when DirCollectionFree() is
called.   

  

  




 **See Also :**


**[DirCollectionFirstEntry](DirCollectionFirstEntry.md)**


**[DirCollectionFree](DirCollectionFree.md)**


**[DirCollectionGetNumEntries](DirCollectionGetNumEntries.md)**


**[DirCollectionNextEntry](DirCollectionNextEntry.md)**



----------------------------------------------------------------------------------------------------------


 





