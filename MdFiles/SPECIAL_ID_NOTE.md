




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



**SPECIAL\_ID\_NOTE** **-** Used in
combination with NOTE\_CLASS\_xxx when calling NSFDbGetSpecialNoteID.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



**Description :**



Define NSF
Special Note ID Indices. The first 16 of these are reserved for "default
notes" in each of the 16 note classes. In order to access these, use
SPECIAL\_ID\_NOTE+NOTE\_CLASS\_xxx.  This is generally used when calling
NSFDbGetSpecialNoteID.  Note: NSFNoteOpen, NSFDbReadObject and NSFDbWriteObject
support reading special notes or objects directly (without calling
NSFDbGetSpecialNoteID). They use a DIFFERENT flag with a similar name:
NOTE\_ID\_SPECIAL (see nsfnote.h).  Remember this rule:  

  

 SPECIAL\_ID\_NOTE is a 16 bit mask and is used as a NoteClass argument.  

 NOTE\_ID\_SPECIAL is a 32 bit mask and is used as a NoteID or RRV argument.  

  

 Note: Whenever a new SPECIAL\_ID is added, the table in \nsf\dbio\dbfhinfo.c
must be updated. This table specifies which note class each SPECIAL\_ID is
treated as for access checking purposes.


 **See Also :**


**[NOTE\_CLASS\_xxx](NOTE_CLASS_xxx.md)**


**[NSFDbGetSpecialNoteID](NSFDbGetSpecialNoteID.md)**



----------------------------------------------------------------------------------------------------------


 





