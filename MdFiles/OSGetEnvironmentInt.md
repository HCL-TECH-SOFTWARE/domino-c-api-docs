




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




 


**Function : OS Environment Variables**



**OSGetEnvironmentInt** **- Return
integer value of an environment variable.**


**----------------------------------------------------------------------------------------------------------**



**#include <osenv.h>**



int
LNPUBLIC **OSGetEnvironmentInt(**  

      char far \*VariableName**);**



**Description :**



OSGetEnvironmentInt
is a wrapper around the API OSGetEnvironmentLong.  It takes the specified
envrironment string, converts the text associated with it into type
"int", and returns that value to the current context.     

  

Domino and Notes environment variables are stored in notes.ini, and can be set
from the Lotus Domino Server via the SET CONFIG console command.  

  

Example (from Server Console):  

SET CONFIG TEST\_INTEGER=100  

  

  

Note: this function is implemented as a macro:  

  

  

#define OSGetEnvironmentInt(s) ((int) OSGetEnvironmentLong(s))


 


**Parameters :**



Input :  

VariableName  -  Pointer to name of the environment variable (null-terminated,
case-insensitive).   

  




Output :  

(routine)  -  Integer value of variable;  0 if variable is not found or is not
numeric.  

  

  




 **See Also :**


**[OSGetEnvironmentLong](OSGetEnvironmentLong.md)**


**[OSGetEnvironmentString](OSGetEnvironmentString.md)**


**[OSSetEnvironmentVariable](OSSetEnvironmentVariable.md)**


**[OSSetEnvironmentInt](OSSetEnvironmentInt.md)**



----------------------------------------------------------------------------------------------------------


 





