




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




**Initial Release 8.5.2**



**Function : Dir**



**DirEntryDelete** **- Helper
functions for the DirModify fields of the DirEntry.** 


**----------------------------------------------------------------------------------------------------------**



**#include <direntry.h>**



STATUS
LNPUBLIC **DirEntryDelete(**  

      DIRENTRY  hEntry**);**



**Description :**



Delete the
Domino entry in the directory which is associated with hEntry. If the entry
exists in a Domino directory then it is deleted. If it exists in an LDAP
directory then only the Domino specific items are deleted from the entry.


 


**Parameters :**



Input :  

hEntry  -  Handle to the entry to delete.  

  




Output :  

(routine)  -  NOERROR   

An ERR status on failure indicating the problem.   

  

  

  




 **See Also :**


**[DirCtxGetEntryByID](DirCtxGetEntryByID.md)**



----------------------------------------------------------------------------------------------------------


 





