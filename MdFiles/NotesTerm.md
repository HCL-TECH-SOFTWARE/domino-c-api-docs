




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




 


**Function : Main Routines**



**NotesTerm** **- Domino
and Notes runtime shutdown routine.**


**----------------------------------------------------------------------------------------------------------**



**#include <global.h>**



void
LNPUBLIC **NotesTerm(**void**);**



**Description :**



This routine
is used only in programs that do NOT have a NotesMain() or AddinMain().


 


      A call
to this routine will shut down the Domino or Notes runtime system.  Other Lotus
C API functions for Domino and Notes cannot be used after calling this routine.



 


      It is
strongly suggested that applications terminate immediately after calling
NotesTerm.   Failing to do so, applications can hold onto resources which
cannot be easily cleaned up in the event of a Notes/Domino crash.


 


**Parameters :**




Output :  

(routine)  -  None.  

  

  




 **See Also :**


**[AddInMain](AddInMain.md)**


**[NotesInit](NotesInit.md)**


**[NotesInitExtended](NotesInitExtended.md)**


**[NotesInitIni](NotesInitIni.md)**


**[NotesMain](NotesMain.md)**



----------------------------------------------------------------------------------------------------------


 





