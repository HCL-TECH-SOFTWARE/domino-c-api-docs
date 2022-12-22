




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




**Initial Release 4.5**



**Symbolic Value : Full Text Search**



**FT\_RESULT\_ENTRY\_xxx** **-** FT\_SEARCH\_RESULT\_ENTRY
Flags.


**----------------------------------------------------------------------------------------------------------**



**#include <ft.h>**


 **Symbolic Values :**      FT\_RESULT\_ENTRY\_RESTRICTED            -  Entry has read
fields.  

  

      FT\_RESULT\_ENTRY\_TITLE\_RESTRICTED             -  Title of Database is
restricted.  

  




**Description :**



These values
describe restrictions in the additional data that follows the
FT\_SEARCH\_RESULT\_ENTRY array that is returned by FTSearch when a search is
performed on a search site database that has a multi-database index.


 **See Also :**


**[FT\_SEARCH\_RESULT\_ENTRY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/59F65E1E7DFF89A98525635F0080BA2A)**



----------------------------------------------------------------------------------------------------------


 





