




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




 


**Data Type : Database Drivers**



**DBVEC** **-** Database
Driver Vector.


**----------------------------------------------------------------------------------------------------------**



**#include
<dbdrv.h>**



**Definition :**



typedef struct dbvec {  

 


   char
ClassName[MAX\_DBDRV\_NAME+1]; /\* name of driver class+'\0' \*/  

 


   HMODULE hModule;                 
/\* hModule of loaded module \*/  

  

   /\* Do per-process initialization routine.  This is called just


      after the
LoadLibrary, and is the first entry point in the


      library.  When
this entry point is called, all of the other


      entry point
vectors are filled in by this routine. \*/  

  

   STATUS (LNCALLBACKPTR Init)(


              struct
dbvec far \*vec);  

  

   /\* Per-process termination routine, ASSUMING that all open


      sessions for this
context have been closed by the time this is


      called.  This is
called just prior to the FreeLibrary. \*/  

  

   STATUS (LNCALLBACKPTR Term)(


              struct
dbvec far \*vec);  

  

   /\* Open a session.  Any databases opened as a side-effect of


      Functions
performed on this session will gather up their


      context in the
hSession returned by this routine. \*/  

  

   STATUS (LNCALLBACKPTR Open)(


              struct
dbvec far \*vec,


             
HDBDSESSION far \*rethSession);  

  

   /\* Close a session, and as a side-effect all databases whose


      context has been
built up in hSession. \*/  

  

   STATUS (LNCALLBACKPTR Close)(


              struct
dbvec far \*vec,


             
HDBDSESSION hSession);  

  

   /\* Set auxiliary context, used principally when called from


      Desk \*/  

  

   STATUS (LNCALLBACKPTR SetOpenContext)(


              struct
dbvec far \*vec,


             
HDBDSESSION hSession,


              char far
\*DefaultDbName,


             
DBOPENBYIDPROC Proc,


              DHANDLE
hNames,


              DWORD
hParentWnd);  

  

   /\* Perform a function on a session.  If any databases must be


      opened as a
side-effect of this function, gather context into


      hSession so that
it may be later deallocated/closed in


      Close. \*/  

  

   STATUS (LNCALLBACKPTR Function)(


              struct
dbvec far \*vec,


              HDBDSESSION
hSession,


              WORD
Function,


              WORD
argc,


              DWORD far
\*argl,


              void far
\* far \*argv,


              DHANDLE
far \*rethResult,


              DWORD far
\*retResultLength);  

  

   /\* Flags \*/  

  

   FLAG fUpdateIfModified:1; /\* TRUE if we want UpdateCollections


                               
if modified \*/  

  

} DBVEC;


 


**Description :**



This data
structure contains definitions required to implement a database driver.  A
database driver is an API program (implemented as an executable program
library) that can read data from non-Domino databases using the @functions,
@DbColumn and @DbLookup.  

  

See the chapter on external database drivers in the *Lotus C API User Guide*
for more information.


 **See Also :**


**[HDBDSESSION](HDBDSESSION.md)**



----------------------------------------------------------------------------------------------------------


 





