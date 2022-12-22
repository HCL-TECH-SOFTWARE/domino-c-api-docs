




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



**OSGetEnvironmentString** **- Gets the
string value of an environment variable.**


**----------------------------------------------------------------------------------------------------------**



**#include <osenv.h>**



BOOL
LNPUBLIC **OSGetEnvironmentString(**  

      const char far \*VariableName,  

      char far \*retValueBuffer,  

      WORD  BufferLength**);**



**Description :**



OSGetEnvironmentString
is used to get the value of a Domino or Notes environment variable string.  It
takes the name of the environment variable, the address of a text buffer (up to
MAXENVVALUE bytes), and the length of that buffer minus one (1).  It returns
the null-terminated string currently associated with the environment variable.  

  

Domino and Notes environment variables are stored in the notes.ini file. 
Environment variables can be set from the Lotus Domino Server Console.  

  

Example:  

  

From Server Console:  

SET CONFIG TEST\_STRING=THIS\_IS\_IT  

  




 


**Parameters :**



Input :  

VariableName  -  Pointer to name of the environment variable (null-terminated,
case-insensitive)  

  

BufferLength  -  (Size of buffer) - 1 (leaving 1 byte for a guaranteed NULL
terminator)  

  




Output :  

(routine)  -  TRUE if specified variable was found, FALSE if not.  

  

  

retValueBuffer  -  The address of an existing text buffer in which the
null-terminated string value of the specified environment variable is
returned.  Caller must preallocate space for the buffer (up to MAXENVVALUE
bytes).  

  




 **See Also :**


**[OSGetEnvironmentLong](OSGetEnvironmentLong.md)**


**[OSSetEnvironmentVariable](OSSetEnvironmentVariable.md)**


**[OSSetEnvironmentInt](OSSetEnvironmentInt.md)**



----------------------------------------------------------------------------------------------------------


 





