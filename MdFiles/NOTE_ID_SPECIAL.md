




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




 


**Symbolic Value : IDs**



**NOTE\_ID\_SPECIAL** **-** Used in
combination with NOTE\_CLASS\_xxx when calling NSFNoteOpen or NIFOpenCollection.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



**Description :**



If
NOTE\_ID\_SPECIAL is OR'ed in with a note class (NOTE\_CLASS\_xxx), the resulting
note ID may be passed into NSFNoteOpen and may be treated as though you first
did an NSFDbGetSpecialNoteID followed by an NSFNoteOpen, all in a single
transaction.


 


If
NOTE\_ID\_SPECIAL is OR'ed with NOTE\_CLASS\_DESIGN, the resulting note ID may be
specified in the ViewNoteID parameter of NIFOpenCollection to open the design
collection.


 **See Also :**


**[NOTE\_CLASS\_xxx](NOTE_CLASS_xxx.md)**


**[NSFDbOpen](NSFDbOpen.md)**


**[NIFOpenCollection](NIFOpenCollection.md)**


**[NSFDbGetSpecialNoteID](NSFDbGetSpecialNoteID.md)**



----------------------------------------------------------------------------------------------------------


 





