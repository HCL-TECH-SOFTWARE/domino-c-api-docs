




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




 


**Symbolic Value : Full Text Search**



**FT\_RESULTS\_xxx** **-** FT\_SEARCH\_RESULTS
Flags.


**----------------------------------------------------------------------------------------------------------**



**#include <ft.h>**


 **Symbolic Values :**      FT\_RESULTS\_SCORES       -  A parallel array of bytes
containing the relevancy scores follow the array of NoteIDs in the
FT\_SEARCH\_RESULTS structure.  

  

      FT\_RESULTS\_EXPANDED   -  Search results are series of
FT\_SEARCH\_RESULT\_ENTRY structures.  

  

      FT\_RESULTS\_URL   -  Search results are in the URL expanded format.   

Search results are returned in one FT\_SEARCH\_URL\_RESULTS and series of
FT\_SEARCH\_URL\_RESULT\_ENTRY structures. This is supported by FTSearchExt only  

  




**Description :**



These values
describe any additional data that may follow the FT\_SEARCH\_RESULTS structure
that is returned by FTSearch or FTSearchExt.


 **See Also :**


**[FT\_SEARCH\_RESULTS](FT_SEARCH_RESULTS.md)**


**[FTSearch](FTSearch.md)**



----------------------------------------------------------------------------------------------------------


 





