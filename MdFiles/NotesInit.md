




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



**NotesInit** **- \*
OBSOLETE \* Notes runtime initialization routine.**


**----------------------------------------------------------------------------------------------------------**



**#include <global.h>**



STATUS
LNPUBLIC **NotesInit(**void**);**



**Description :**



NotesInit()
is obsolete;  this function has been replaced by NotesInitExtended(). 
NotesInit() is supported under OS/2 and Windows for backwards compatibility. 
API programs that run under other operating systems, such as Unix, and use
main() as the entry point, should call NotesInitExtended() rather than
NotesInit().   

  

If your program uses NotesInit(), then after all your program's Notes API calls
have returned, but before your program exits, call NotesTerm().  

  

NotesInit() locates the Notes program and Notes data directories and reads the
notes.ini file. NotesInit() returns an error (a non-zero status) if, for
example, Notes is not installed.


 


**Parameters :**




Output :  

(routine)  -  A non-zero return value indicates that the Notes runtime did not
initialize properly.  

  

  




 **See Also :**


**[AddInMain](AddInMain.md)**


**[NotesInitExtended](NotesInitExtended.md)**


**[NotesInitThread](NotesInitThread.md)**


**[NotesMain](NotesMain.md)**


**[NotesTerm](NotesTerm.md)**


**[NotesTermThread](NotesTermThread.md)**



----------------------------------------------------------------------------------------------------------


 





