




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




 


**Function : OS File**



**OSGetDataDirectory** **- Get the
pathname of the local Domino or Notes data directory.**


**----------------------------------------------------------------------------------------------------------**



**#include <osfile.h>**



WORD
LNPUBLIC **OSGetDataDirectory(**  

      char far \*retPathName**);**



**Description :**



Given the
address of a text buffer, this function returns the path specification of the
local Domino or Notes data directory.  It also returns the length of that
null-terminated string.  OSGetDataDirectory is equivalent to using
OSGetEnvironmentString to obtain the value of the "Directory=" environment
variable from notes.ini.


 


**Parameters :**




Output :  

(routine)  -  The length of the returned data directory path specification.  

  

  

retPathName  -  The address of a text buffer dimensioned with MAXPATH, in which
a null-terminated string containing the full path specification of the LOCAL
Domino or Notes data directory is returned.  

  




 **See Also :**


**[NSFDbPathGet](NSFDbPathGet.md)**


**[NSFDbLocateByReplicaID](NSFDbLocateByReplicaID.md)**


**[NSFDbOpen](NSFDbOpen.md)**


**[NSFDbOpenExtended](NSFDbOpenExtended.md)**


**[OSPathNetConstruct](OSPathNetConstruct.md)**


**[OSPathNetParse](OSPathNetParse.md)**


**[OSGetEnvironmentString](OSGetEnvironmentString.md)**



----------------------------------------------------------------------------------------------------------


 





