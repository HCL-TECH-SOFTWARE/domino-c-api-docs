




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




**Initial Release 4.0**



**Function : Main Routines**



**NotesInitThread** **- Thread
initialization routine**


**----------------------------------------------------------------------------------------------------------**



**#include <global.h>**



STATUS
LNPUBLIC **NotesInitThread(**void**);**



**Description :**



Initialize
the Domino or Notes runtime system to support a new thread.  Applications may
makeC API calls from more than one thread.  Each new thread must call
NotesInitThread() before making any other C API calls.


 


      The
first thread calls NotesInitExtended which does the process initialization as
well as the the initialization for that thread.  Each subsequent thread must
call NotesInitThread and, before terminating, each subsequent thread must call
NotesTermThread.  The last thread out must call NotesTerm.  However, the thread
that calls NotesInitExtended does not have to be the thread that calls
NotesTerm.


 


**Parameters :**




Output :  

(routine)  -  NOERROR if successfull, or a non-zero return value if unable to
initialize thread state.  

  

  




 **See Also :**


**[NotesInitExtended](NotesInitExtended.md)**


**[NotesTerm](NotesTerm.md)**


**[NotesTermThread](NotesTermThread.md)**



----------------------------------------------------------------------------------------------------------


 





