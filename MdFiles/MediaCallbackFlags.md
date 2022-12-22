




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 6**



**Data Type : Backup**



**MediaCallbackFlags** **-** Media
callback flags.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdb.h>**



**Definition :**




typedef
enum {


        MediaCallback\_NoteUpdate
= 0x01,      /\* Update of existing Note \*/


        MediaCallback\_NoteInsert
= 0x02,      /\* Addition of new note \*/


        MediaCallback\_NoteDelete
= 0x04,      /\* Delete of note \*/


        MediaCallback\_CLR       
= 0x08       /\* Event is the undo of an action due to some failure \*/


}
MediaCallbackFlags;


 


**Description :**



Values from this
enumeration type are returned by NOTESRESTORECALLBACKFUNCTION to indicate the
type of action performed on a particular note during media recovery.  The
action types are:


 


MediaCallback\_NoteUpdate
- Update of existing note.


 


MediaCallback\_NoteInsert
- Addition of new note.


 


MediaCallback\_NoteDelete
- Deletion of note.


 


MediaCallback\_CLR
- Event is the undo of an action due to some failure.


 **Sample Usage :**



switch
(state\_flags)


{


        case
MediaCallback\_NoteInsert:


         
strcpy(note\_action, "Addition");


         
break;


 


        case
MediaCallback\_NoteDelete:


         
strcpy(note\_action, "Deletion");


         
break;


 


        case
MediaCallback\_CLR:


         
strcpy(note\_action, "Undo");


         
break;


 


        default:


         
strcpy(note\_action, "Unknown");


}


 **See Also :**


**[NOTERESTORECALLBACKFUNCTION](NOTERESTORECALLBACKFUNCTION.md)**


**[NSFRecoverDatabasesWithCallback](NSFRecoverDatabasesWithCallback.md)**



----------------------------------------------------------------------------------------------------------


 





