




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




 


**Data Type : IDs**



**GLOBALINSTANCEID** **-** Globally
identifies an instance of a note.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



typedef struct {  

   DBID     File;   /\* database Creation time/date \*/  

   TIMEDATE Note;   /\* note Modification time/date \*/  

   NOTEID   NoteID; /\* note ID within database \*/  

} GLOBALINSTANCEID;


 


**Description :**



This
structure globally identifies an instance of a note across databases. If we are
doing a SEARCH\_ALL\_VERSIONS, the note with the latest modification date is the
one that is the "most recent" instance.


 **See Also :**


**[NSFNoteGetInfo](NSFNoteGetInfo.md)**



----------------------------------------------------------------------------------------------------------


 





