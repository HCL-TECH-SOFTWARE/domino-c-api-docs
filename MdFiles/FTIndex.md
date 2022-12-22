




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




 


**Function : Full Text Search**



**FTIndex** **- Indexes a
local database for full text searching capabilities.**


**----------------------------------------------------------------------------------------------------------**



**#include <ft.h>**



STATUS
LNPUBLIC **FTIndex(**  

      DBHANDLE  hDB,  

      WORD  Options,  

      char far \*StopFile,  

      FT\_INDEX\_STATS far \*retStats**);**



**Description :**



This
function creates a new full text index for a local database.    

  

Full text indexing of a remote database is not supported in the C API.


 


**Parameters :**



Input :  

hDB  -  The handle to the open database.  

  

Options  -  Indexing options.  See Symbolic Value, FT\_INDEX\_xxx.  These options
may be or'd together.  

  

StopFile  -  Domino and Notes R5 no longer use a Stop Word file.  Pass in NULL
for this parameter.  In preveious releases of Domino and Notes, you could
specify the name of the Stop Word file or pass in NULL for this parameter if
there was no Stop Word file.  A Stop Word file contains words that were not to
be indexed.    

  




Output :  

(routine)  -    Return status of the call - indicates either success or what
the error is. The return codes include:  

  

NOERROR  

  

ERR\_xxx - Error returned by lower level functions. Call OSLoadString to
interpret the code.  

  

  

retStats  -  Pointer to returned indexing statistics.  Pass in NULL if no
statistics are desired.  

  




 **See Also :**


**[FT\_INDEX\_STATS](FT_INDEX_STATS.md)**


**[FT\_INDEX\_xxx](FT_INDEX_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





