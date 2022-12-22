




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




**Initial Release 4.5**



**Function : OS Program**



**OSLoadProgram** **- Load and
execute an external Program.**


**----------------------------------------------------------------------------------------------------------**



**#include <osmisc.h>**



STATUS
LNPUBLIC **OSLoadProgram(**  

      char far \*filename,  

      char far \*WorkingDir,  

      char far \*Arguments,  

      WORD  Flags**);**



**Description :**




This
function loads and executes an external Program. Use OSLoadProgram to load and
execute software modules at run time.   

  

OSLoadProgram provides C API programs with a platform-independent procedure for
loading and executing a program.


 


Starting
with Release 4.6, the command line is assumed to be in LMBCS, the Lotus
Multi-Byte Character Set, and is translated to the operating system's native
character set before being passed to the called program.


 


 


**Parameters :**



Input :  

filename  -  File name of the executable program to load and execute.  

  

WorkingDir  -  If "WorkingDir" is not NULL, the specified directory
is made to be the current directory before program execution, else it is the
directory that the program lives in.  

  

Arguments  -  Optional command line arguments to be used when launching the
program.  The command line arguments are translated from LMBCS to the native
character set.  

  

Flags  -  Define how to execute the program. Use one of the OS\_LOADPROG\_xxx
flags symbolic values.  

  




Output :  

(routine)  -  Completion status of the operation, NOERROR if successful.  

  

  




 **Sample Usage :**



STATUS           error;  

char     ProgramPath[MAXPATH];  

WORD Flags = OS\_LOADPROG\_BACKGROUND | OS\_LOADPROG\_ICONIC |  

                                                            OS\_LOADPROG\_DEBUG;


 


/\*
Set your program  pathname  ProgramPath \*/


           
< ..............>


 


/\*
Load the program  with "-w" command line argument: \*/


  

            error = OSLoadProgram(ProgramPath, NULL, "-w", Flags);


 


 **See Also :**


**[OS\_LOADPROG\_xxx](OS_LOADPROG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





