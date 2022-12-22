




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




**Initial Release 6.0.3**



**Symbolic Value : Database**



**GETNOTES\_xxx** **-** Control
flags for NSFDbGetNotes.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**


 **Symbolic Values :**      GETNOTES\_PRESERVE\_ORDER    -  Preserve order of notes in
NoteID list.  

  

      GETNOTES\_SEND\_OBJECTS         -  Send (copiable) objects along with note.  

  

      GETNOTES\_ORDER\_BY\_SIZE        -  Order returned notes by (approximate)
ascending size.  

  

      GETNOTES\_CONTINUE\_ON\_ERROR         -  Continue to next on list if error
encountered.  

  

      GETNOTES\_GET\_FOLDER\_ADDS   -  Enable folder-add callback function after
the note-level callback.  

  

      GETNOTES\_APPLY\_FOLDER\_ADDS           -  Apply folder ops directly - don't
bother using callback.  

  

      GETNOTES\_NO\_STREAMING         -  Don't stream - used primarily for
testing purposes.  

  




**Description :**



Control
flags for NSFDbGetNotes.


 **See Also :**


**[NSFDbGetNotes](NSFDbGetNotes.md)**



----------------------------------------------------------------------------------------------------------


 





