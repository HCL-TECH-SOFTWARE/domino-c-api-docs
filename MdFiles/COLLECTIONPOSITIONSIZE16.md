




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




 


**Function : Views**



**COLLECTIONPOSITIONSIZE16** **- Computes
space used by a COLLECTIONPOSITION16.**


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**



int **COLLECTIONPOSITIONSIZE16(**  

      COLLECTIONPOSITION16 \*collpos**);**



**Description :**



A macro used
to compute the size of the portion of a COLLECTIONPOSITION16 structure that is
actually used.  This is only necessary when collection positions are packed
into a buffer in less space than using the COLLECTIONPOSITION16 structure (e.g.
NIFReadEntries).  

  

#define COLLECTIONPOSITIONSIZE16(p) (sizeof(DWORD) \* ((p)->Level+2))


 


**Parameters :**



Input :  

collpos  -  Pointer to a COLLECTIONPOSITION16.  Note : The Level and Tumbler
array values for the COLLECTIONPOSITION16 must have been previously assigned.  

  




Output :  

(routine)  -  Returns size of the COLLECTIONPOSITION16 structure in bytes.  

  

  




 **See Also :**


**[NIFOpenCollection](NIFOpenCollection.md)**


**[NIFReadEntries](NIFReadEntries.md)**



----------------------------------------------------------------------------------------------------------


 





