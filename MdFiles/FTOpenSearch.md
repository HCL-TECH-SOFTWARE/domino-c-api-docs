




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



**FTOpenSearch** **- Opens a
full text search handle.**


**----------------------------------------------------------------------------------------------------------**



**#include <ft.h>**



STATUS
LNPUBLIC **FTOpenSearch(**  

      DHANDLE far \*rethSearch**);**



**Description :**



This routine
opens a full text search handle that is used in FTSearch.  After the search is
completed, use FTCloseSearch to close the full text search handle and
deallocate the memory associated with it.


 


**Parameters :**




Output :  

(routine)  -  Return status of the call - indicates either success or what the
error is. The return codes include:  

  

NOERROR  

  

ERR\_xxx - Error returned by lower level functions. Call OSLoadString to
interpret the code.  

  

  

rethSearch  -  Pointer to returned search handle to be passed into FTSearch. 
The returned handle could be zero.  

  




 **See Also :**


**[FTCloseSearch](FTCloseSearch.md)**


**[FTSearch](FTSearch.md)**


**[FTSearchExt](FTSearchExt.md)**



----------------------------------------------------------------------------------------------------------


 





