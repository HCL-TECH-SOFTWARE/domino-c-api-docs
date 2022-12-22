




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



**Function : Database**



**DirCollectionNextEntry** **- Find the
next entry after the "current" entry in the hCollection collection.** 


**----------------------------------------------------------------------------------------------------------**



**#include <dircoll.h>**



DIRENTRY
LNPUBLIC **DirCollectionNextEntry(**  

      DIRCOLLECTION  hCollection**);**



**Description :**



Find the
next entry after the "current" entry in the hCollection collection. 


**Warning:** 


This
function is not re-entrant! Always use the DirCollectionNthEntry() [E:\temp\dir\html\dircoll\_8h.html
- 4d86c64b487c4900a4b6c4d8eb0bfba9](file:///E:/temp/dir/html/dircoll_8h.html#4d86c64b487c4900a4b6c4d8eb0bfba9)function if the collection is
shared amongst processes or threads!


 


**Parameters :**



Input :  

hCollection  -  Handle to the collection of entries to be navigated.  

  




Output :  

(routine)  -  A reference to the next match in hCollection. This uses and
updates the collection's internally maintained "current" directory
entry cursor. If there are no more entries in the collection then NULLDIRENTRY
will be returned. If the input hCollection is NULLDIRCOLLECTION then the return
value is NULLDIRENTRY.   

DirEntryFree() may be called on the returned directory entry object to remove
it from the collection. Or, the entry will be freed when DirCollectionFree() is
called.   

  

  




 **See Also :**


**[DirCollectionFirstEntry](DirCollectionFirstEntry.md)**


**[DirCollectionFree](DirCollectionFree.md)**


**[DirCollectionGetNumEntries](DirCollectionGetNumEntries.md)**


**[DirCollectionNthEntry](DirCollectionNthEntry.md)**



----------------------------------------------------------------------------------------------------------


 





