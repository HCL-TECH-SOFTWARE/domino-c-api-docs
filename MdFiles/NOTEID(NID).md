




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



**NOTEID ( NID )** **-** Note ID
within a database.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



typedef DWORD NOTEID;


 


**Description :**



A NOTEID
identifies a particular note within a given database. Use a NOTEID and a
database handle to open a note.  

  

A NOTEID is a file position that is guaranteed never to change within the
database.  It does not contain information about which database the note
resides in. The NOTEID does not change when the note is modified. Two replica
copies of the same note, in two separate replica databases, will most likely
have different NOTEIDs.


 **See Also :**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[ORIGINATORID](ORIGINATORID.md)**


**[UNIVERSALNOTEID](UNIVERSALNOTEID.md)**



----------------------------------------------------------------------------------------------------------


 





