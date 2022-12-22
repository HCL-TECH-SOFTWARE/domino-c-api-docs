




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




 


**Symbolic Value : Note**



**IDTABLE\_xxx** **-** IDTable -
Flags


**----------------------------------------------------------------------------------------------------------**



**#include <idtable.h>**


 **Symbolic Values :**      IDTABLE\_MODIFIED            -  modified - set by
Insert/Delete and can be cleared by caller if desired.  

  

      IDTABLE\_INVERTED           -  sense of list inverted (reserved for use by
caller only).  

  




**Description :**



These
defines are used in conjunction with IDTableFlags and IDTableSetFlags.


 **Sample Usage :**


    

   

   if (IDTableFlags(idtable\_ptr) & IDTABLE\_MODIFIED)  

       /\* Well we didn't,so NSFDbGetModifiedNoteTable() must have \*/  

       /\* Will clear modified flag for our own puposes            \*/  

       IDTableSetFlags(idtable\_ptr, 0);  

  




 **See Also :**


**[IDTableFlags](IDTableFlags.md)**


**[IDTableSetFlags](IDTableSetFlags.md)**



----------------------------------------------------------------------------------------------------------


 





