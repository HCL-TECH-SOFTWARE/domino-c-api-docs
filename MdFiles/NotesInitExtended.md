




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




 


**Function : Main Routines**



**NotesInitExtended** **- Domino or
Notes runtime initialization routine**


**----------------------------------------------------------------------------------------------------------**



**#include <global.h>**



STATUS
LNPUBLIC **NotesInitExtended(**  

      int  argc,  

      char far \* far \*argv**);**



**Description :**



This routine
initializes the Notes runtime system for all environments.  This function also
replaces NotesInit() on Windows systems.  This routine can also be used for
standalone programs running with Domino.  

  

API programs that start with main() must call NotesInitExtended() before
calling any other C API functions.   After completing all C API actions and
before the program exits, call NotesTerm().  

  

NotesInitExtended uses argv[0] to attempt to locate the Domino or Notes
executable directory.   If the Domino or Notes executable directory is not in
argv[0], then NotesInitExtended will use the path to determine the Domino or
Notes executable directory. Then it performs the same initialization that
NotesInit() performs.   As of release 5 of Domino and Notes, you can specify an
ini file to NotesInitExtended, by passing an argument preceded by an
"=" sign.  This argument can be any argument except the first
argument.  The name of the ini file may include the full path specification. 
If the path is not included then the specified ini file must reside in the
Domino or Notes executable directory.  Use the following syntax followed by the
file name in the argv list: example "=new.ini".  

  

Applications may use more than one thread of execution accessing Domino or
Notes.  Each new thread created by an application must call NotesInitThread()
before making calls to Domino or Notes and NotesTermThread() before the thread
terminates.  Please refer to the reference entries for these functions for more
information.  

  

NotesInitExtended uses argv[0] to locate the Domino or Notes executable
directory and the resource directory. Then it performs the same initialization
that NotesInit() performs.  To specify an ini file to NotesInitExtended, you
may now pass an argument preceded by an "=" sign in Release 5.0.  This
argument can be any argument except the first argument.  The name of the ini
file may include the full path specification.  If the path is not included then
the specified ini file must reside in the Domino or Notes executable
directory.  Use the following syntax followed by the file name in the argv
list: example "=new.ini".  

  

Applications may use more than one thread of execution accessing Domino or
Notes.  Each new thread created by an application must call NotesInitThread()
before making calls to Domino or Notes and NotesTermThread() before the thread
terminates.  Please refer to the reference entries for these functions for more
information.


 


**Parameters :**



Input :  

argc  -  The number of command line arguments the program was invoked with.  

  

argv  -  Far pointer to an array of far pointers to null-terminated character
strings that contain the arguments the program was invoked with.  

  




Output :  

(routine)  -  NOERROR if successfull, or a non-zero return value if unable to
initialize the Domino or Notes runtime system.  

  

  




 **Sample Usage :**


/\* Initialize Notes for
any platform. \*/  

  

    error = NotesInitExtended (argc, argv);  

  

    if (error)  

    {  

        fprintf (stderr, "\nError initializing Notes.\n");  

        exit (EXIT\_FAILURE);  

    }


 **See Also :**


**[NotesTerm](NotesTerm.md)**


**[NotesInitThread](NotesInitThread.md)**


**[NotesTermThread](NotesTermThread.md)**



----------------------------------------------------------------------------------------------------------


 





