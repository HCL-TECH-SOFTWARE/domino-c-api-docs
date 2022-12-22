




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



**NotesInitIni** **- \*
OBSOLETE \* Initialize Notes using alternate .ini file.**


**----------------------------------------------------------------------------------------------------------**



**#include <global.h>**



STATUS
LNPUBLIC **NotesInitIni(**  

      char far \*pConfigFileName**);**



**Description :**



\*\*\*OBSOLETE
- Included for backward compatibility only\*\*\*


 


NotesInitIni
essentially performs the same function as NotesInit with the additional
capability of being able to specify the notes.ini file.  It  is supported under
OS/2 and Windows 32-bit applications only and is an alternative to NotesInit
and to NotesInitExtended.    API programs that run under other operating
systems, such as UNIX, must not call this function.  As of R5.0 of the Lotus C
API for Domino and Notes, you may specify the notes.ini file with
NotesInitExtended on all platforms.


 


This routine
initializes the Domino or Notes runtime system using the specified file in
place of notes.ini.  API programs that start with main()  and need to use
NotesInitIni, must call NotesInitIni before calling any other C API
functions.   After completing all C API actions and before the program exits,
call NotesTerm.  Call this routine once and only once per task.   

  

Applications may use more than one thread of execution accessing Domino or
Notes.  Each thread must call NotesInitThread before making calls to Notes and
NotesTermThread before the thread terminates.


 


**Parameters :**



Input :  

pConfigFileName  -  Pointer to the null-terminated pathname of the alternate
initialization file.  

  




Output :  

(routine)  -  (routine)  -  NOERROR if successfull, or a non-zero return value
if unable to initialize the Notes runtime system.  

  

  




 **See Also :**


**[NotesInit](NotesInit.md)**


**[NotesInitExtended](NotesInitExtended.md)**


**[NotesTerm](NotesTerm.md)**


**[NotesInitThread](NotesInitThread.md)**


**[NotesTermThread](NotesTermThread.md)**



----------------------------------------------------------------------------------------------------------


 





