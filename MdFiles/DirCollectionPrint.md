




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



**DirCollectionPrint** **- Prints a
DIRCOLLECTION's contents using a supplied println() routine.**


**----------------------------------------------------------------------------------------------------------**



**#include <dircoll.h>**



void
LNPUBLIC **DirCollectionPrint(**  

      const DIRCOLLECTION  hCollection,  

      int  printflags,  

      DIRPRINTLN\_PROC  println,  

      void \*ctx**);**



**Description :**



Prints a
DIRCOLLECTION's contents using a supplied println() routine.


 


**Parameters :**



Input :  

hCollection  -  Directory collection to print  

  

printflags  -  OR-ed set of DIRPRINT\_FLAG values  

  

println  -  Print routine (e.g., DirPrintln())  

  

ctx  -  println()-specific context  

  




 


 **See Also :**


**[DirCollectionFirstEntry](DirCollectionFirstEntry.md)**


**[DirCollectionFree](DirCollectionFree.md)**


**[DirCollectionGetNumEntries](DirCollectionGetNumEntries.md)**


**[DirCollectionNextEntry](DirCollectionNextEntry.md)**


**[DirCollectionNthEntry](DirCollectionNthEntry.md)**



----------------------------------------------------------------------------------------------------------


 





