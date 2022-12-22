




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



**DirCollectionFirstEntry** **- Find the
first entry in the hCollection collection.** 


**----------------------------------------------------------------------------------------------------------**



**#include <dircoll.h>**



DIRENTRY
LNPUBLIC **DirCollectionFirstEntry(**  

      DIRCOLLECTION  hCollection**);**



**Description :**



This
function sets the "current" entry to the first entry and then
retrieves it.


Warning:This function is not re-entrant! Always use the
DirCollectionNthEntry() [E:\temp\dir\html\dircoll\_8h.html
- 4d86c64b487c4900a4b6c4d8eb0bfba9](file:///E:/temp/dir/html/dircoll_8h.html#4d86c64b487c4900a4b6c4d8eb0bfba9)function if the collection is
shared amongst processes or threads!


 


**Parameters :**



Input :  

hCollection  -  Handle to the collection of entries to be navigated.  

  




Output :  

(routine)  -  A reference to the first entry in hCollection. This sets the
collection's internally maintained "current" directory entry cursor.
If the input hCollection is NULLDIRCOLLECTION then the return value is
NULLDIRENTRY.   

DirEntryFree() may be called on the returned directory entry object to remove
it from the collection. Or, the entry will be freed when DirCollectionFree() is
called.   

  

  




 **See Also :**


**[DirCollectionGetNumEntries](DirCollectionGetNumEntries.md)**


**[DirCollectionNextEntry](DirCollectionNextEntry.md)**



----------------------------------------------------------------------------------------------------------


 





