




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



**Symbolic Value : OS Program**



**OS\_LOADPROG\_xxx** **-** OSLoadProgram
- Flags


**----------------------------------------------------------------------------------------------------------**



**#include <osmisc.h>**


 **Symbolic Values :**      OS\_LOADPROG\_ICONIC     -  Don't show application window  

  

      OS\_LOADPROG\_BACKGROUND     -  Don't bring to the foreground  

  

      OS\_LOADPROG\_DEBUG     -  Start with QNC  

  

      OS\_LOADPROG\_DETACHED          -  Don't wait around for this process to
exit  

  

      OS\_LOADPROG\_ASSOCIATE          -  Look for a file type association  

  

      OS\_LOADPROG\_PRIORITY\_LOW   -  Start process with a lower priority  

  

      OS\_LOADPROG\_SHELL\_SCRIPT\_USE\_EXECVP    -  Flag to signal a shell script,
so we can use execvp instead of execv. Currently in use only on AIX  

  

      OS\_LOADPROG\_OPEN\_WITH         -  Flag to add the necessary things to do
an open with command. Currently on use only on NT  

  




**Description :**



These
symbols define how to execute the program in a call to OSLoadProgram.


 **See Also :**


**[OSLoadProgram](OSLoadProgram.md)**



----------------------------------------------------------------------------------------------------------


 





