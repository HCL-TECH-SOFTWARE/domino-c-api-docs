




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




 


**Function : OS Library**



**OSLoadLibrary** **- Load a
library module and get the main entry point function**


**----------------------------------------------------------------------------------------------------------**



**#include <osmisc.h>**



STATUS
LNPUBLIC **OSLoadLibrary(**  

      const char far \*LibraryName,  

      DWORD  Flags,  

      HMODULE far \*rethModule,  

      void far \*retEntryPoint**);**



**Description :**



This
function loads the specified library module and returns a pointer to the main
entry point function in the library.  Use OSLoadLibrary to load and execute
software modules at run time.   

  

OSLoadLibrary provides C API programs with a platform-independent procedure for
loading and executing library modules dynamically at run time.  Under Windows,
this function results in a call to the function LoadLibrary (see the Microsoft
Windows SDK Reference).   

  

OSLoadLibrary can be used to load any library module that is identified to your
program at run time.  For example, C API programs can use OSLoadLibrary to load
Notes import/export libraries.  


 


**Parameters :**



Input :  

LibraryName  -  File name of the executable program library module to load.  

  

Flags  -  Reserved;  must be 0.  

  




Output :  

(routine)  -  Completion status of the operation, NOERROR if successful.  

  

  

rethModule  -  Receives the module handle of the loaded library. Under Windows
this is the instance handle of the loaded library.  Under UNIX, the HMODULE is
an identifier provided by Domino.  Use the returned hModule in subsequent calls
to OSFreeLibrary.  

  

retEntryPoint  -  Receives the address of the main entry point to the loaded
library.  Under Windows, this is the ordinally first entry point exported by
the Dynamic Link Library.  Under other operating systems, this is the function
with name "MainEntryPoint". The syntax for calling this function must
be set by convention.  Specifically, the syntax of the main entry point to
Notes import/export library modules is defined by Data Type IXENTRYPROC.  

  




 **See Also :**


**[IXENTRYPROC](IXENTRYPROC.md)**



----------------------------------------------------------------------------------------------------------


 





