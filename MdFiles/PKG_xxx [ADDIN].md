




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




 


**Symbolic Value : Resource Definition**



**PKG\_xxx [ADDIN]** **-** Base value
for an AddIn's error definitions.


**----------------------------------------------------------------------------------------------------------**



**#include <globerr.h>**



**Description :**



When
developing C API programs to run under Windows, define a string table by
creating a resource (.RC) file and use PKG\_ADDIN as the base value for the
resource IDs in the string table.  

  

By convention, the first resource ID in a C API program's string table should
be PKG\_ADDIN, and the corresponding string should be the name of the API
program.  The second ID should be PKG\_ADDIN+1, and the corresponding string
should describe the API program's version number.  Subsequent IDs should be
numbered sequentially after that (PKG\_ADDIN+2, PKG\_ADDIN+3, etc...).  

  

Lotus Domino Server AddIn programs under Windows should follow this
convention.  By default, Domino  uses the string at offset PKG\_ADDIN in the
string table associated with a server AddIn program as the task name in the
status line in the "show tasks" display.  Server AddIn programs under
other operating systems should use AddInCreateStatusLine.


 **Sample Usage :**


(in HISTERR.H)  

#define HISTORY\_NAME                       (PKG\_ADDIN+0)  

#define HISTORY\_VERSION                    (PKG\_ADDIN+1)  

#define DEFAULT\_HISTORY\_DBFILENAME         (PKG\_ADDIN+2)  

#define DEFAULT\_HISTORY\_DBSERVER           (PKG\_ADDIN+3)  

  

(in HISTORY.RC)  

#include <windows.h>  

#include <globerr.h>  

#include "history.h"  

#include "histerr.h"  

  

STRINGTABLE  

BEGIN  

HISTORY\_NAME, "History Sample Program"  

HISTORY\_VERSION, "Version 1.0"  

DEFAULT\_HISTORY\_DBFILENAME, "history"


 **See Also :**


**[AddInFormatError](AddInFormatError.md)**


**[AddInLogError](AddInLogError.md)**


**[AddInSetStatus](AddInSetStatus.md)**


**[AddInCreateStatusLine](AddInCreateStatusLine.md)**


**[STATUS](STATUS.md)**



----------------------------------------------------------------------------------------------------------


 





